---
title: "Ubuntu 9.04 i386 on hp pav8387ea (amd64)"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by kerzane on 2009-11-30
Hi,

I have a HP pavilion dv8387ea.

I was running 9.04 amd64, but was having some problems with wireless, and also wanted to convert back to the i386 version to access some software like acroread etc.

Now that I have installed the i386 version, my wireless is not working. The panel applet has a red and white cross, and the lshw output indicates the wireless card is disabled, although the driver is apparently fine. The wireless button has no effect in ubuntu, and the problem is irrespective of whether the button is on or off in windows.

Is my problem fundamental, or is it a symptom of running a 32bit os on a 64bit machine? (i thought this wouldn't be a problem, but maybe i was wrong?) 

Thanks,
Kerzane.

---

### Post by gordintoronto on 2009-11-30
I can't help with the wireless, although I would be very surprised if your problem is due to running a 32-bit OS on a 64-bit machine.

I am running 9.04 64-bit, and Acroread works perfectly for me.  It's version 9.2, dated 10/6/2009.  I think I downloaded it from the repositories.

---

### Post by jdstunner on 2009-11-30
-kerzane

Try running *ifconfig* *-a* in the terminal. This will print a list of network devices installed on the computer.

The one for your wireless should read "wlan0" or similar.

Then type this in the terminal:

[I]sudo ifconfig wlan0 up

[/I]That should enable your device so you can browse wireless networks in the area.

---

### Post by kerzane on 2009-12-02
@gordintoronto

ok, I don't understand that, my understanding was that acroread and other applications weren't available for the 64 bit version.

@jdstunner

thanks for that, I had high hopes that this would work, but alas...
Output is

SIOCSIFFLAGS: No such file or directory

Any other ideas?

Many thanks, 
kerzane.

---

### Post by jdstunner on 2009-12-02
Could you please print a copy of the output of this command:* ifconfig -a*

---

### Post by kerzane on 2009-12-02
Yep, 

when I get home. 

From a google search of the output of "sudo ifconfig wlan0 up" it seems to be a driver problem. I'll follow this up later.

Thanks,
Kerzane.

---

### Post by jdstunner on 2009-12-02
Ha! I did the same. A google search on your error output provided a number of forums related to the issue. Although I did not find one cause and one resolution. 

Here are a collected list of commands to help you figure some things out. You may also run a *man* page on any of these commands to learn more. Most of these commands need to be run with sudo to work. 

```

man <command>

ifconfig <interface> up
ifconfig <interface> down

## print all interfaces ##
ifconfig -a 

## print connected interfaces ##
ifconfig

## check for dhcp ##
dhclient

```Good luck! If you are still stuck, post your *ifconfig -a *and *dhclient*.

---

### Post by gordintoronto on 2009-12-02
> **kerzane said:**
> @gordintoronto

ok, I don't understand that, my understanding was that acroread and other applications weren't available for the 64 bit version.


It's in the repository, I installed it, it works just fine.  It is my default PDF viewer, and I view new PDFs a couple of times a day on average.

---

