---
title: "bluetooth problem"
date: 2013-05-27
forum: Networking &amp; Wireless
---

### Post by amiralex32 on 2013-05-27
i have tried to transfer file using bluetooth after upgrading to ubuntu 13.04 this error message appear
GDBUS.ERROR:org.openbex.error.failed:unable to request session
please help to solve this problem

[COLOR=#000000]i have tried this ommand[/COLOR]
[COLOR=#000000]obexftp -b [address of the phone] -p file.ext[/COLOR]
[COLOR=#000000]Try `obexftp --help' for more information.[/COLOR]
[COLOR=#000000]Try `obexftp --help' for more information.[/COLOR]
[COLOR=#000000]Try `obexftp --help' for more information.[/COLOR]
[COLOR=#000000]Scanning for [address ...[/COLOR]
[COLOR=#000000]Browsing [address ...[/COLOR]
[COLOR=#000000]Connecting...failed: connect[/COLOR]
[COLOR=#000000]Tried to connect for 0ms[/COLOR]
[COLOR=#000000]error on connect(): Invalid argument[/COLOR]
[COLOR=#000000]Still trying to connect[/COLOR]
[COLOR=#000000]Connecting...failed: connect[/COLOR]
[COLOR=#000000]Tried to connect for 0ms[/COLOR]
[COLOR=#000000]error on connect(): Invalid argument[/COLOR]
[COLOR=#000000]Still trying to connect[/COLOR]
[COLOR=#000000]Connecting...failed: connect[/COLOR]
[COLOR=#000000]Tried to connect for 0ms[/COLOR]
[COLOR=#000000]error on connect(): Invalid argument[/COLOR]
[COLOR=#000000]Still trying to connect[/COLOR]
[COLOR=#000000]amiralex@amir-pc:~$ obexftp -b [address of the phone] -p file.ext[/COLOR]
[COLOR=#000000]Try `obexftp --help' for more information.[/COLOR]
[COLOR=#000000]Try `obexftp --help' for more information.[/COLOR]
[COLOR=#000000]Try `obexftp --help' for more information.[/COLOR]
[COLOR=#000000]Scanning for [address ...[/COLOR]
[COLOR=#000000]Browsing [address ...[/COLOR]
[COLOR=#000000]Connecting...failed: connect[/COLOR]
[COLOR=#000000]Tried to connect for 0ms[/COLOR]
[COLOR=#000000]error on connect(): Invalid argument[/COLOR]
[COLOR=#000000]Still trying to connect[/COLOR]
[COLOR=#000000]Connecting...failed: connect[/COLOR]
[COLOR=#000000]Tried to connect for 0ms[/COLOR]
[COLOR=#000000]error on connect(): Invalid argument[/COLOR]
[COLOR=#000000]Still trying to connect[/COLOR]
[COLOR=#000000]Connecting...failed: connect[/COLOR]
[COLOR=#000000]Tried to connect for 0ms[/COLOR]
[COLOR=#000000]error on connect(): Invalid argument[/COLOR]
[COLOR=#000000]Still trying to connect[/COLOR]
[COLOR=#000000]amiralex@amir-pc:~$ hcitool scan[/COLOR]
[COLOR=#000000]Scanning ...[/COLOR]
[COLOR=#000000]amiralex@amir-pc:~$[/COLOR]

---

### Post by slickymaster on 2013-05-27
What are you using to send files via bluetooth?```
sudo rfkill list
```will show you if bluetooth is softblocked. If it says 'Yes' then try:```
sudo rfkil unblock bluetooth
```
Other than that, you can check an already reported bug: [Bug #1148033]("https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/1148033"), particularly you might want to see post [#23]("https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/1148033/comments/23") as it might provide a workaround for it.

---

### Post by amiralex32 on 2013-05-27
i  have tried this ommand
obexftp -b [address of the phone] -p file.ext
Try `obexftp --help' for more information.
Try `obexftp --help' for more information.
Try `obexftp --help' for more information.
Scanning for [address ...
Browsing [address ...
Connecting...failed: connect
Tried to connect for 0ms
error on connect(): Invalid argument
Still trying to connect
Connecting...failed: connect
Tried to connect for 0ms
error on connect(): Invalid argument
Still trying to connect
Connecting...failed: connect
Tried to connect for 0ms
error on connect(): Invalid argument
Still trying to connect
amiralex@amir-pc:~$ obexftp -b [address of the phone] -p file.ext
Try `obexftp --help' for more information.
Try `obexftp --help' for more information.
Try `obexftp --help' for more information.
Scanning for [address ...
Browsing [address ...
Connecting...failed: connect
Tried to connect for 0ms
error on connect(): Invalid argument
Still trying to connect
Connecting...failed: connect
Tried to connect for 0ms
error on connect(): Invalid argument
Still trying to connect
Connecting...failed: connect
Tried to connect for 0ms
error on connect(): Invalid argument
Still trying to connect
amiralex@amir-pc:~$ hcitool scan
Scanning ...
amiralex@amir-pc:~$

i have tried to install the package blueman

sudo apt-get install blueman 
the bluetooth is working well but i have 2 icon for bluetooth one is the oldest one which is working also and a new one after installing the package what shall i do

---

### Post by slickymaster on 2013-05-27
Install the blueman package, it's in the repositories so you can install it via the software center or running the following command in a terminal window:```
sudo apt-get install blueman
```Once you have it installed just reboot your computer and you should be ready to go.

---

