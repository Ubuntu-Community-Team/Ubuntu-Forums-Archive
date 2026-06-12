---
title: "another low resolution problem"
date: 2010-01-15
forum: Multimedia Software
---

### Post by onefr on 2010-01-15
Hi

I have read quite a number of posts where people are having problems with low resolution, unfortunately none quite like problem.

After installing Ubuntu 9.10 I am unable to get any resolution higher than 800x600.  I followed some Ubuntu wiki pages and tried to xrandr --addmode and I get the following error.

X Error of failed request: BadName (named color or font does not exist)
Major opcode of failed request: 151 (RANDR)
Minor opcode of failed request: 16 (RRCreateMode)
Serial number of failed request 18
Current serial number in output stream: 18

my output for lspci | grep VGA is:

01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

I don't have an xorg.conf file in /etc/X11

Please would advise on possible solutions.

---

