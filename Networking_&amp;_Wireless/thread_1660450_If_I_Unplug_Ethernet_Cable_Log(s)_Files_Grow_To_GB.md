---
title: "If I Unplug Ethernet Cable Log(s) Files Grow To GB In Size Quickly"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by war59312 on 2011-01-05
Hello,

So last night I unplugged the Internet and left my laptop on.

I wake up 8 hours later and I have a warning on my screen stating only 945kb of free space. OMG, wtf!

So I click the analyze button and turns out it's these log files:

/var/log/kern.log
/var/log/messages
/var/log/ufw.log

Each one is 2.2GB in size.

/var/log/syslog.1 is another 1.3GB file.

So something is causing these logs to happen when Ethernet is unplugged. :(

I'm guessing it's because I'm running local DNS?

Thanks for the help,

Will

---

### Post by JeffDavidoff on 2011-01-06
Please show some extract of those big log files. These files will contain the hint what caused the fill up.

---

### Post by war59312 on 2011-01-11
Looks like it's UFW's fault, seems it's logging everything. :(

> Jan 11 13:53:55 will-linux-laptop kernel: [ 8626.978773] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=213 TOS=0x00 PREC=0x00 TTL=64 ID=62629 DF PROTO=TCP SPT=47785 DPT=58491 WINDOW=192 RES=0x00 ACK PSH URGP=0

Jan 11 13:53:55 will-linux-laptop kernel: [ 8626.978798] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=213 TOS=0x00 PREC=0x00 TTL=64 ID=62629 DF PROTO=TCP SPT=47785 DPT=58491 WINDOW=192 RES=0x00 ACK PSH URGP=0

Jan 11 13:53:55 will-linux-laptop kernel: [ 8626.978837] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=19919 DF PROTO=TCP SPT=58491 DPT=47785 WINDOW=530 RES=0x00 ACK URGP=0

Jan 11 13:53:55 will-linux-laptop kernel: [ 8626.978856] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=19919 DF PROTO=TCP SPT=58491 DPT=47785 WINDOW=530 RES=0x00 ACK URGP=0So just ran [FONT=monospace]"[/FONT]sudo ufw logging off", will see what happens.

Seems to have worked. :D

---

