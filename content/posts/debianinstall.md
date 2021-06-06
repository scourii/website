---
title: "Debian Vs. AMD Hardware"
draft: false
date: 2021-05-31T23:13:40
---
Today I installed Debian on a really shitty laptop that I was asked to fix. It's running with 4GB of RAM, along with a Quad-Core 2GHz AMD chip, and a Radeon HD 8400, or in basic terms, a really outdated laptop for today's standards, with 2013(?) specs. The laptop was running Windows 10, which is probably the worst OS to use on extremely outdated software due to the amount of background processes that Windows 10 has. The computer could barely open things like File Explorer in a minute, and a browser was even worse. I decided to install Debian SID on it, because of how stable Debian is, and because I like having the most up to date packages, which is what SID provides. I ended up installing XFCE, because it's very light, and can be customized to look comfy. I went forward with the installation, and it installed perfectly fine, but once I booted into it, I started having some problems, specifically with firmware. The laptop wouldn't even boot into TTY mode, I would see a screen full of kernel panic messages / a ```Radeon kernel modesetting for r600 or later requires firmware-amd-graphics``` error message, and then a cursor blinked at the top left part of the screen. What I did first, was reboot into recovery mode. This allowed me to interact with the Operating System, through TTY. I then added ```deb http://deb.debian.org/debian/ sid main contrib non-free
deb-src http://deb.debian.org/debian/ sid main contrib non-free``` to ```/etc/apt/sources.list```, and thought I fixed the issue. However, as I tried to update the system, I noticed that I wasn't connected to the internet for some reason, even though I had an ethernet cable plugged in for faster download speeds. What I had to do, was modify the ```/etc/resolv.conf``` file and added ```nameserver 8.8.8.8``` for and IPv4 conncetion, since there was none. I then used ```systemctl restart network``` to see if the internet worked now, which it did. After the internet was working, I could update the system to SID, and get all the updated packages. Once everything was updated, I did a quick ```sudo apt-get update && sudo apt-get install firmware-amd-graphics``` and rebooted, and then I could login to the XFCE desktop environment without any issues. The laptop now runs at 300MB on idle, opens up applications much faster, and it's actually functional now.