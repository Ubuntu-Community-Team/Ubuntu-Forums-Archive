---
title: "[SOLVED] lirc serial ir blaster issues [7.10]"
date: 2008-03-18
forum: Mythbuntu
---

### Post by syphr42 on 2008-03-18
I have been using Knoppmyth for MythTV for a few years now, but the rest of my home network is running Ubuntu (a few desktops, a laptop, and a few servers), so I have been wanting to start using Mythbuntu.

Well, I took the plunge this past weekend and installed 7.10 (I can't risk an alpha install right now). For the most part everything went OK (minor mishap with GRUB writing to the wrong disk and blowing away the LVM metadata on my 750GB drive, but an LVM backup was able to get it running again). I upgraded to 0.21 as well right after the install and that went fine.

However, one thing I can not get working is my serial IR blaster for changing channels on my Comcast Motorola box. I have tried everything I can think of, including re-compiling LIRC and lirc_serial. I know the hardware is working, because I can boot the Knoppmyth install CD, drop to a console and run the irblaster setup script and "irsend -d /dev/irblasterd SEND_ONCE DCT2000 1" changes to channel one on my cable box.

As you can see, I am using a standard LIRC remote config (DCT2000).  When I recompiled LIRC, I added debugging. Here is the output on the daemon side, and then the irsend side:

lircd-0.8.2[7484]: lircd(serial) ready
lircd-0.8.2[7484]: registering local client
lircd-0.8.2[7484]: accepted new client on /dev/lircd1
lircd-0.8.2[7484]: driver supports both sending and receiving
lircd-0.8.2[7484]: received command: "SEND_ONCE DCT2000 1"
lircd-0.8.2[7484]: clearing transmit buffer
lircd-0.8.2[7484]: adding to transmit buffer: 9036
lircd-0.8.2[7484]: adding to transmit buffer: 4424
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 4424
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 2185
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 2185
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 2185
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 2185
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 2185
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 2185
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 2185
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 2185
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 2185
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 2185
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 2185
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 4424
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 4424
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 4424
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: adding to transmit buffer: 4424
lircd-0.8.2[7484]: adding to transmit buffer: 556
lircd-0.8.2[7484]: transmit buffer ready
lircd-0.8.2[7484]: removed client


./irsend -d /dev/lircd1 SEND_ONCE DCT2000 1
buffer: -BEGIN-
buffer: -SEND_ONCE DCT2000 1-
buffer: -SUCCESS-
buffer: -END-


As you can see, there are no obvious errors (at least not obvious to me), but nothing happens. If anyone knows of anything that may shed light on the problem, I would greatly appreciate it. I feel stuck here and if I can't get it working, I'll have to abandon Mythbuntu, which would be a last resort.

Also, please note two other points:
First, I have a Hauppauge PVR-350 whose remote is using /dev/lircd (the silver dogbone remote) and it has worked flawlessly since I installed Mythbuntu.

Secondly, I have used setserial for uart none on my COM1 (/dev/ttyS0) and I have created a file at /etc/modprobe.d/lirc_serial as follows:

$ cat /etc/modprobe.d/lirc_serial 
alias char-major-61 lirc_serial
options lirc_serial irq=4 io=0x3f8


Thanks!

---

### Post by syphr42 on 2008-03-19
In a last ditch effort, I tried compiling the latest CVS snapshot (0.8.3pre1) and to my amazement, everything started working! I guess there is something my install of Mythbuntu does not like about 0.8.2. Anyway, it works now!

---

### Post by spiregrain on 2008-03-29
I found I could get it to work with the current Hardy pre-release by editing the /etc/modprobe.d/lirc-serial so that it contains:

```
#COM1 equivalent, /dev/ttyS0
options lirc_serial irq=4 io=0x3f8 softcarrier=1
#COM2 equivalent, /dev/ttyS1
#options lirc_serial irq=3 io=0x2f8
/etc/modprobe.d/lirc-serial 
```

---

### Post by superm1 on 2008-03-29
> **spiregrain said:**
> I found I could get it to work with the current Hardy pre-release by editing the /etc/modprobe.d/lirc-serial so that it contains:

```
#COM1 equivalent, /dev/ttyS0
options lirc_serial irq=4 io=0x3f8 softcarrier=1
#COM2 equivalent, /dev/ttyS1
#options lirc_serial irq=3 io=0x2f8
/etc/modprobe.d/lirc-serial 
```
Thanks.  This should be automatic in the last kernel upload coming up soon.

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy-lum.git;a=commit;h=31e0aaef38231f8fcf7213604499e59f0751fbdc](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy-lum.git;a=commit;h=31e0aaef38231f8fcf7213604499e59f0751fbdc)

---

### Post by atkellyx on 2008-04-08
Yep thanks very much, this got me going too (after much frustration).

My steps were as follows:

1. download, extract, configure and compile lirc 0.8.3pre2 for homebrew serial receiver
2. created file /etc/modprobe.d/lirc_serial
3. put following in file:
options lirc_serial irq=4 io=0x3f8 softcarrier=1

Interestingly, these are the options I choose when configuring lirc before compilation, I guess this just forces the issue when the module is loaded.

4.  Execute these comands:
setserial /dev/ttyS0 uart none
modprobe lirc_serial
lircd -d /dev/ttyS0

lircd is now running

5.  irrecord -d /dev/lirc0 /tmp/testIR

I now get output in irrecord, I can get 2 rows of dots but doesn't go further at this point but at least irrecord is seeing some IR activity.  I also seem to have some stability problems with the entire system temporarily hanging for a few seconds every now and then when lirc is running, but I think I've seen this posted as another problem.  Hopefully they will have the answer.

Now that this works, I thought I'd try the apt-get version of lirc instead of compiling but this did not work.  It wasn't until I followed my successful steps above that I noticed that removal of my version of lirc removed the /etc/modprobe.d/lirc_serial file, so the apt-get lirc version may still work with this.

Incidentally, I am using Hardy as I could not get lirc working in Gutsy.  I wish I'd seen this thread before.


Hope this helps someone.

---

### Post by lift28 on 2008-07-25
thanks:)

---

