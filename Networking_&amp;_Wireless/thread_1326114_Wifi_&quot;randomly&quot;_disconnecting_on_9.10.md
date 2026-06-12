---
title: "Wifi &quot;randomly&quot; disconnecting on 9.10"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by aryzing on 2009-11-14
We all know that there is nothing random about computer errors, yet i have not been able to reproduce mine consistently:
The Wifi "randomly" disconnects with karmic and i can't connect again to ANY network, yet i see them all. It repeatedly asks me to introduce the password again, and i do, and it just keeps on trying to connect without success. However, with 9.04 i had absolutely no problems.. ever!
Is there any command i could issue when the problem occurs to provide any additional info?

OS: 9.10 64bit
Model: Acer Extensa 5230.

Thanks

---

### Post by jnorthr on 2009-11-14
networking in 9.10 does not seem as reliable as 9.04. How is your signal strength ? Is there any way you can move the wireless box to a different location. It may be too near other metal objects, so make it harder to work, yes i know this is a lame idea but worth a shot.

dmesg will show the joblog and some of the messages that occur when things happen. This might give us some further clues.

---

### Post by aryzing on 2009-11-14
Some final thoughts: 9.04 was 32 bit, 9.10 is 64bit
Wired connections works fine

---

### Post by aryzing on 2009-11-14
@jnorthr
I tried that. Perhaps i should have been more explicit: my problem is not only with my home network, its with all wireless networks i try connecting to.

---

### Post by aryzing on 2009-11-14
The final output of dmesg is in the attatched file (i could not enter the full report because of size limit on attatched txt's. I am no expert on reading such reports, however to the end there are a great number of failures, and something about ethernet connection, which might be when i decided to connect the ethernet cable after the wireless dropped again.

---

### Post by hal10000 on 2009-11-14
I have made the experience that uninstalling that crappy network-manager and installing wicd instead solved all wireless problems.

---

### Post by audacs on 2009-11-14
I also just uninstalled network-manager and install wicd. Seems to be running much better and it has easy access to lots of settings.

---

### Post by phishie on 2009-11-14
> **aryzing said:**
> The final output of dmesg is in the attatched file (i could not enter the full report because of size limit on attatched txt's. I am no expert on reading such reports, however to the end there are a great number of failures, and something about ethernet connection, which might be when i decided to connect the ethernet cable after the wireless dropped again.


Karmic seems to have problems with Atheros wireless. The problem exists in Jaunty as well in my case. I solved it by install the wireless drivers in the backport. This can be done by running in your terminal:

```
*sudo apt-get install linux-backports-modules-karmic*
```I'm not sure if that command still works, but if it doesn't, try

```
*sudo apt-get install linux-backports-modules*
```The problem went away after I installed the driver.

I hope this helps you =)

---

### Post by robth on 2009-11-14
I think this might be related to [my issue]("http://ubuntuforums.org/showthread.php?p=8298159").

---

### Post by aryzing on 2009-11-14
I have just finished installing wicd and so far so good. I believe i will make this my default choice from now on.

Thankyou so much for the help!

Just one final thought: with network-manager i had a small icon on my panel which changed acording to signal strength. Is it possible (and desirable) to have such an icon? - Thanks once again

---

### Post by hal10000 on 2009-11-14
> Just one final thought: with network-manager i had a small icon on my panel which changed acording to signal strength. Is it possible (and desirable) to have such an icon? - Thanks once again

If you are running gnome you may install the gdeklets package, which provides a lot of useful spplets (including wireless) for your desktop.

Btw., if you still get network-timeouts, then you should consider posting #8

---

### Post by aryzing on 2009-11-15
actually never mind, on restarting the computer i got an icon. The world is now perfect :)

cheers

---

### Post by Dale61 on 2009-11-15
> **hal10000 said:**
> I have made the experience that uninstalling that crappy network-manager and installing wicd instead solved all wireless problems.

Thx hal, that fix worked for me (so far!)[-o<

---

### Post by salous on 2009-11-19
I have this annoying issue too on Ubuntu 9.10,
My wireless works perfectly on Ubuntu 9.04 and Arch Linux,
Must be the network-manager.

---

### Post by dnvikram on 2010-02-01
> **phishie said:**
> Karmic seems to have problems with Atheros wireless. The problem exists in Jaunty as well in my case. I solved it by install the wireless drivers in the backport. This can be done by running in your terminal:

```
*sudo apt-get install linux-backports-modules-karmic*
```I'm not sure if that command still works, but if it doesn't, try

```
*sudo apt-get install linux-backports-modules*
```The problem went away after I installed the driver.

I hope this helps you =)

Yesterday,I performed an online upgrade of my 9.04 to 9.10 and started seeing this irritating wifi issue.In my case it drops atleast once in every 10minutes and only reboot fixes it.Looks like Atheros wifi cards have issue in 9.10.It used to work like a charm in 9.04..Will try installing the backports today and if that doesnt work,will have to uninstall network manager and install wicd.

---

### Post by dnvikram on 2010-02-02
> **dnvikram said:**
> Yesterday,I performed an online upgrade of my 9.04 to 9.10 and started seeing this irritating wifi issue.In my case it drops atleast once in every 10minutes and only reboot fixes it.Looks like Atheros wifi cards have issue in 9.10.It used to work like a charm in 9.04..Will try installing the backports today and if that doesnt work,will have to uninstall network manager and install wicd.

That did it.Installing the backports and rebooting the machine seems to have fixed the issue.Didnt have a single wifi drop this time and it was at 100% signal strength all the time unlike before.The wifi worked even after bringing back the system from standby/suspend.

---

