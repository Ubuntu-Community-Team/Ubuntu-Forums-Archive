---
title: "Creative Zen X-Fi MP3Player?"
date: 2008-08-21
forum: Multimedia Software
---

### Post by |cJ| on 2008-08-21
Hey Guys

Have seached but not found any threads about the Creative Zen X-fi in Ubuntu/Linux. Im running ubuntu/xfce, have tried Gnomad2 but it wont see it..

I brought it assuming it would work and now im a bit stuck.. Any ideas about how to get linux to see it? all I want to do is dump all my music on the thing.. I assumed it would come up as mass storaage device but apparently thats asking to much :(

---

### Post by smokingwreckage on 2008-08-21
I've had no luck getting my 4 gig Zen to go into "docked" mode. It realizes its plugged in and begins charging but no dice on actually syncing any music.

---

### Post by kam.samji on 2008-09-02
> **smokingwreckage said:**
> I've had no luck getting my 4 gig Zen to go into "docked" mode. It realizes its plugged in and begins charging but no dice on actually syncing any music.

I've just got the 8GB Zen X-Fi and have only just noticed that it is charging, ,but Ubunutu has not picked it up!!!

Will try and play around....

---

### Post by mcallenSchmee on 2008-09-04
You could try Amarok, Banshee, or Rhythmbox. They all connect to my Zen (it's not an X-Fi though).

> **smokingwreckage said:**
> I've had no luck getting my 4 gig Zen to go into "docked" mode. It realizes its plugged in and begins charging but no dice on actually syncing any music.

What are you doing? Just plugging it in? It's an mtp device, so you need to use a program like those I mentioned above.

---

### Post by pankaj85 on 2008-09-08
Hi cJ..

I am using creative zen x=fi on my ubuntu... You got to install libmtp to get it working... also i use Gnomad2 to transfer my data.... just starting with Gnomad doesn't work for me:( so i use "sudo gnomad2"... then it detect the player and everything just works fine... :guitar:

---

### Post by chandra on 2008-09-17
Perhaps this might help:

[http://ubuntuforums.org/showthread.php?p=5734480](http://ubuntuforums.org/showthread.php?p=5734480)

---

### Post by b3n87 on 2008-09-22
To get a Zen working, you have to plug it in and then it starts charging. Then you have to open Rhythmbox manually with the MTP plugin enabled and then it mounts it.

Im interested to know if this will work with the X-Fi too as I would like one myself.

Let me know if the above method works :)

---

### Post by kakemann on 2008-10-06
With that method I can access it using gnomad2, but not Rhythmbox. Any suggestions as to why that happends?

---

### Post by b3n87 on 2008-10-15
> **kakemann said:**
> With that method I can access it using gnomad2, but not Rhythmbox. Any suggestions as to why that happends?

Did you enable the MTP plugin from the Rhythmbox plugin menu? I had to do that to get it to work

---

### Post by kakemann on 2008-10-16
Yes I have it enabled.

---

### Post by tarini on 2008-11-14
guys i've love you!! using gnomad2 i can upload my mp3s!!!

but i've got some question...
1- which groups have i to set for my user for using gnomad2 without sudoing it?
2- what about video? have you tried to upload succesfully??
3- in rhythmbox (launched with sudo) i've click on "scan removable media" but it tells me nothing (mtp plugin is installed)
4- how can i merge cd cover in my mp3s??

thanks again... really! :)

---

### Post by jdpearson on 2008-12-07
> **pankaj85 said:**
> Hi cJ..

I am using creative zen x=fi on my ubuntu... You got to install libmtp to get it working... also i use Gnomad2 to transfer my data.... just starting with Gnomad doesn't work for me:( so i use "sudo gnomad2"... then it detect the player and everything just works fine... :guitar:

I thought this was going to work for me, but alas it did not. I have a new Zen X-Fi 16GB.  It starts to work, and the Zen even shows up Docked for a moment, then goes black.  Gnomad says it's scanning but after it "finishes" I don't have anything new in Gnomad to indicate I've actually scanned my Zen. 

The terminal reports the following:

Device 0 (VID=041e and PID=4162) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session


Any ideas?

---

### Post by jdpearson on 2008-12-09
Ok, I got it working with Amarok using the instructions at:
[http://ubuntuforums.org/showthread.php?p=5734480](http://ubuntuforums.org/showthread.php?p=5734480) with a the minor change that the file to edit is actually /etc/udev/rules.d/45-libmtp8.rules

However, it still doesn't work in Rythymbox which I'd like to try.  I DO have the MTP plugin in checked but it doesn't find the device.  

Any other ideas?

---

### Post by lavinog on 2008-12-09
I am having a problem with my zen x-fi
with it plugged in, and I type:
```
sudo lsusb -vd 014e:4162
```
my zen x-fi will crash and will require a reset.
I have tried the clean up and have tried it on 8.10 64bit and 8.04 32bit (three different machines.)

My question is if this is limited to just my zen, or if it does the same thing with yall too?

On two computers I have modified rules in /etc/udev to add the x-fi so i can use it without sudo...both these computers will crash the unit without the need for sudo...another computer wasn't set up this way and wont crash the x-fi without sudo, but will when sudo is used.

---

### Post by jdpearson on 2008-12-10
I did have this same issue until I followed the instructions above to get Amarok to recognize it.  Now I have to find some time to get it to work in Rythmbox.

---

### Post by heroes on 2010-02-05
great info here
didnt know there were so many people trying to contact their zen x-fi player to linux :D

---

### Post by heroes on 2010-02-05
it should be fairly easy to use Gnomad2

---

### Post by lavinog on 2010-02-05
Since Jaunty it has been working fine.
This thread is pretty old.

---

