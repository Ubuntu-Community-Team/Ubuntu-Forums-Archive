---
title: "how to end nc -l if there is nothing to listen"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by gian on 2010-05-22
hello All,

I need to log random events from a serial device.

My Ubuntu 10.4 server has a crontab entry that listen every ten minutes to a serial to ethernet converter, and should append the logs to a file.

nc -l 9999 >> /home/me/log/gate.log

This command works fine from the terminal, but if I paste it in the crontab it does not work.

I think that if the wait is longer than ten minutes, I should add a timeout switch, i.e. if there is nothing to listen, it should drop off before the new crontab comes up.

I tried "-w 30" to end the job, but it just doesn't work, even from terminal.

I'm a bit confused because there are three different netcat in the Unix world...

I'll be very interested to read your comments...

-Gian

---

