---
title: "i ruined my sound driver totally"
date: 2009-01-20
forum: Multimedia Software
---

### Post by Santooka on 2009-01-20
Dear all,

after sending beginning this thread:[http://ubuntuforums.org/showthread.php?p=6585610#post6585610]("http://ubuntuforums.org/showthread.php?p=6585610#post6585610") and no one answered me, i decided to do it myself, so i ruined my sound settings totally and i dunno what to do, how to get it back like it was, where to look at....

so can anybody drive me out of this?

I NEED MY SOUND BACK PLEASE!!!!

---

### Post by cariboo on 2009-01-20
It would help if you could tell us what you have done to get you to the point where you are, so that we get an idea of where to start.

Jim

---

### Post by Santooka on 2009-01-20
cool now i reinstalled the linux image 2.6.24-11 ad it works again


but still no surround

i have 4.1 speakers

i am trying everything written on the internet to do it and nothing yet

ask for whatever files outputs and i will deliver it here but i really need a solution for this

best regards

---

### Post by Santooka on 2009-01-20
ok i tried this :[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/]("http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/")

and tried to install this: [http://paste.ubuntuusers.de/raw/393727/]("http://paste.ubuntuusers.de/raw/393727/") after downloading the package, this is where i totally ruined my sound....

and after fixing it i tried other diofferent things buty alot of threads are talking about the 5.1 and 7.1 speakers and channels, and i guess they differ from the 4.1, right? i dunno

so do u have any ideas what to do ?

---

### Post by cariboo on 2009-01-20
You   do realize that the drivrs you installed are available in the rpeositories. Open System-->Administration-->Synaptic package Manager and search for alsa-base, this includes the needed drivers.

In a Applications-->Accessories-->Terminal type:

```
sudo lshw -C multimedia
```

and paste the output in your next post. The above information will help us solve your problem.

Jim

---

### Post by Santooka on 2009-01-21
here's what i got:

```
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

---

### Post by cariboo on 2009-01-21
Double-click the speaker icon in the top panel and make sure all the controls are turned right up. Also go to System-->Preference-->Sound, and make sure all the outputs are set to autodetect.

Jim

---

### Post by Santooka on 2009-01-21
done, but what mixer do i choose?

i chose HDA Intel (Alsa mixer), right?

anyways it didn't do anything

---

### Post by Santooka on 2009-01-21
yeah i guess it's the right one

---

### Post by cariboo on 2009-01-22
So are you saying your sound now  works?

JIm

---

### Post by Santooka on 2009-01-22
NOOOOOOOOOOO

the sound works fine from the beginning but the thing is with the rear speakers, they r not working at all....

i only hear them click at the booting and shutting down the computer, except that nothing...

---

### Post by Santooka on 2009-01-23
so no better ideas yet??

i never knew this will be a a hard difficult problem like it is right now

---

### Post by Santooka on 2009-01-24
so .................
nothing?

---

### Post by cariboo on 2009-01-27
Can you post a screenshot of what you see when you click on System-->Preferences-->Sound?

Jim

---

### Post by Santooka on 2009-01-28
here it is, but note that i tried to change the device several times and nothing changed :s

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=101331&d=1233186286[/IMG]

---

### Post by cariboo on 2009-01-28
It looks like your outputs are detected properly, so it is just a matter of getting the volume turned up. Strangely I get two different result from alsamixer and gnome-aslamixer, see screenshot. I would suggest using gnome-alsmixer to see if you can turn the other outputs up.

Jim

---

### Post by Santooka on 2009-01-29
here's how it looks for me

---

### Post by cariboo on 2009-02-03
I noticed you have side and lfe turned down, maybe you should turn them up.

Jim

---

