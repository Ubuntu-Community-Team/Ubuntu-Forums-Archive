---
title: "connecting win7 to ubuntu through VNC"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by bennyhay on 2010-10-13
Hi am using win7 trying to connect to a ubuntu box using vnc. I managed  to get it working for me with the full gui viewable. Then one of my  housemates played around with some display settings for the backround  and all of a sudden vnd only comes up with a terminal. 

I went into terminal and attempted to start gdm and got this output

[COLOR=Red]root@ben-desktop:/home/ben# gdm start

** (gdm-binary:21376): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:21376): WARNING **: Could not acquire name; bailing out
root@ben-desktop:/home/ben#

[COLOR=Black]my ssh works fine using putty. I have looked in my /etc/gdm/custom.conf and this is the contents: 
have i got anything wrong in there or am i missing any statements?
[/COLOR][/COLOR]
[COLOR=Red][daemon]
RemoteGreeter=/usr/lib/gdm/gdmlogin
AutomaticLoginEnable=true
AutomaticLogin=ben
TimedLoginEnable=true
TimedLogin=ben
TimedLoginDelay=10

DefaultSession=xubuntu

[security]
AllowRoot=true
AllowRemoteRoot=true
AllowRemoteAutoLogin=true
PasswordRequired=true

[xdmcp]

DisplaysPerHost=1

Enable=true
Port=177
[/COLOR]
Any ideas would be much appreciated. cheers

---

### Post by bennyhay on 2010-10-13
also when i try to run the vnc server with this code, i get the message server is already running
[COLOR=Red]
 vncserver :1 -geometry 1024x768 -depth 16 -pixelformat rgb565[/COLOR]

[COLOR=Black]when i look at ps -al to see processes i get this output:
[COLOR=Red]
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 S     0  3214  3143  0  80   0 -  1159 wait   pts/4    00:00:00 su
0 S     0  3221  3214  0  80   0 -  1148 wait   pts/4    00:00:00 bash
4 S     0  3940  3861  0  80   0 -  1159 wait   pts/0    00:00:00 su
0 S     0  3948  3940  0  80   0 -  1168 n_tty_ pts/0    00:00:00 bash
4 R     0 21419  3221  0  80   0 -   625 -      pts/4    00:00:00 ps
[/COLOR]
so doesnt appear to be running
[/COLOR]

---

### Post by LebLinux on 2010-11-08
Hello, could anyone help connect to ubuntu 10.04 from windows 7 using vncviewer 4. I could connect but all I see is an empty display.
Here is the xstartup config file and the screenshot. I ran vncserver from the terminal as:  vncserver :1 -geometry 1024x768 -depth 16

xstartup file:  [http://pastebin.com/emANxMd8]("http://pastebin.com/emANxMd8")

---

