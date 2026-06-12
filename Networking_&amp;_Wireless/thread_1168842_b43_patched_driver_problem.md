---
title: "b43 patched driver problem"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by chrismiller on 2009-05-24
I installed ubuntu 8.10 on my friends laptop, and he asked me to install kismet and aircrack, but I am having problems setting up the wireless card.

```
jon@jon-laptop:lspci

02:00.0 Network controller:  Broadcom Corporation BCM4312 802.11b/g (rev  01)
```lspci shows the wireless card, and it works out of the box. Setting the card to monitor gives the following error, which I assume means the wireless driver needs to be patched to allow injection?

```
jon@jon-laptop:~$ iwconfig eth1 mode monitor
Error for wireless request "Set  Mode" (8B06) :
    SET failed on device eth1 ; Operation not  permitted.
```
I read in another post that the lw module should be blacklisted becuase it interferes with aircrack.

I added lw to 
/etc/modprobe.b/blacklist

When I modprobe for the wireless driver I get the following output.

```
modprobe b43
WARNING:  /etc/modprobe.d/blacklist line 47: ignoring bad line starting with  'wl'
```I also instaled b43-fwcutter, which as I understand firmware for the wifi card?

I have searched for the solution to my problem, but I am still not understanding how to fix my problem. I would appreciate any help, thanks. :)

---

### Post by Ayuthia on 2009-05-24
From the message that you are getting from the blacklist, it appears that you left out the word blacklist before the wl:
```
blacklist wl
```

The other thing that you will need to verify is if the card has a 14e4:4315 chipset (via lspci -nn).  If it does, the b43 module does not support that card and kismet and aircrack will not work with it.  However, if it is a 14e4:4312, it should be ok.

Since you are seeing eth1 instead of wlan0, I am thinking that you are currently using the wl module to make the card work.  If that is the case, blacklisting the module will stop your card from working.  I am sure that you are aware of this, but I just wanted to put it out there just in case.

---

### Post by chrismiller on 2009-05-27
Thank you for the reply, how do I find out which chipset I have.

Also, in my blacklist file, I list wl at the end of the file on a separate line. Is this incorrect?

Thanks again.

---

### Post by chili555 on 2009-05-30
> Also, in my blacklist file, I list wl at the end of the file on a separate line. Is this incorrect?No.

On a separate line, you need to have:```
blacklist wl
```Not just the 'wl' part.> how do I find out which chipset I have.I think you already know:> 02:00.0 Network controller:  Broadcom Corporation BCM[COLOR="Red"]4312[/COLOR] 802.11b/g (rev  01)> However, if it is a 14e4:[COLOR="Red"]4312[/COLOR], it should be ok.

---

### Post by Ayuthia on 2009-05-30
Actually, to find out the chipset that you have, you will need to use:
```
lspci -nn
```
The 4312 that you are currently seeing is the model name for the card.  The 4312 rev 01 card can come as a 14e4:4312 or a 14e4:4315.  Sorry for the late reply.

---

