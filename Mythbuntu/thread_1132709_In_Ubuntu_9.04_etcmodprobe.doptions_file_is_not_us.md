---
title: "In Ubuntu 9.04 /etc/modprobe.d/options file is not used"
date: 2009-04-22
forum: Mythbuntu
---

### Post by AJ1000 on 2009-04-22
I have a Nova-T-500 (original one) which required the following line in the options file:

options dvb-usb-dib0700 force_lna_activation=1

I tried upgrading to 9.04 and found the options file has been removed. Does anyone know where I should put the above line?

---

### Post by superm1 on 2009-04-22
All files in that directory need a .conf appended.  Just make a new one and call it like nova.conf

---

### Post by superm1 on 2009-04-22
Also, can you please update any wiki or what not that you found that is referring to /etc/modprobe.d/options to reflect this information? 


Thanks

---

### Post by AJ1000 on 2009-04-23
Unfortunately, it did not work, with the Nova-T 500 Dual DVB-T still being in a cold state. Any other ideas? Should there be an update in another file so that mythbuntu knows that nova.conf exists?

---

### Post by AJ1000 on 2009-04-23
I copied the contents of options.dpkg-bak to nova.conf and it is working. I hope this helps others.

---

### Post by utar on 2009-04-23
> **AJ1000 said:**
> Unfortunately, it did not work, with the Nova-T 500 Dual DVB-T still being in a cold state. Any other ideas? Should there be an update in another file so that mythbuntu knows that nova.conf exists?

That line in options.conf will have no effect on changing the Nova from the cold state.  Can you post the relevant line from dsemg, try typing "dmesg | grep dvb" into a terminal.

[Edit: I see you have the card working]


Utar

---

### Post by AJ1000 on 2009-04-23
I did do dmseg | grep dvb, when I reported the initial problem.

However, now that I have copied all the contents of options.dpkg-bak to nova.conf, it does go to the warm state. There was no error (when I reported it was in cold state), just the following line now appears that was missing before:


dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.


Because stuff in options.dpkg-bak was missing, I was not getting a signal lock.

Note: The 'found ... in warm state' line is displayed after the downloading firmware from 'dvb-usb-dib0700-1.20.fw' line.

---

### Post by leafpaul on 2009-04-25
On install 9.04 creates a file called options.dpkg-dist (with the original options file being renamed options.dpkg-bak).  The new options file appears not to be read as adding the amplification line to it did not result in the signal from the tuner card being amplified.

To get the amplification line read I copied the options.dpkg-dist file to options.conf and added the line below to the file:

options dvb_usb_dib0700 force_lna_activation=1

All the files above are in /etc/modprobe.d/

I'm not sure if the options.dpkg-dist is being used by any other processes which is why I copied it rather than renaming it but I would guess that if all files in this directory need to end in .conf then, presumably, it is not being read.

---

### Post by digizone on 2009-04-27
Should this work the same way with a new install as with the above upgrade?

options.dpkg-dist does not appear to be included on a new install. So it can't be copied across and then edited to turn on the LNA.

---

### Post by ddrichardson on 2009-04-27
> **superm1 said:**
> Also, can you please update any wiki or what not that you found that is referring to /etc/modprobe.d/options to reflect this information? 


Thanks
I've taken ownership of this and raised it as an ubuntu-docs bug against the wiki, there are *a lot* of pages that are incorrect so this may take some time but we're busy cleaning up the site any way.

---

### Post by dsbw on 2009-10-10
I stumbled across a solution to a problem I have with my KWorld/Hauppauge set-up (while looking for something else, too, I feel like I won the lottery!) that keeps them from swapping device assignments on reboot.

> Add an option line to your ivtv module in modprobe.conf
options ivtv ivtv_first_minor=1

And I'm trying to figure out from this thread where that would go. And not having any luck. :)

---

### Post by eliofall on 2009-11-02
/home/{you user name}/v4l-dvb/linux/Documentation/video4linux/bttv/Modprobe.conf

thatis where mine is found but yours might be in a different spot. just search for Modprobe.conf in file system 'more options>show hidden files" and you'll find where you installed it

---

### Post by utar on 2009-11-02
> **dsbw said:**
> I stumbled across a solution to a problem I have with my KWorld/Hauppauge set-up (while looking for something else, too, I feel like I won the lottery!) that keeps them from swapping device assignments on reboot.



And I'm trying to figure out from this thread where that would go. And not having any luck. :)

I have a similar line for my sat card on 8.04, however I have it in /etc/modprobe.d/options (I believe this should be options.conf on 9.10), and not in a modprobe.conf file in my home directory.  I would be surprised if it would work in your home directory as this is a system wide option, where you need to be root to change.

[Edit: I think on 9.10 any *.conf file in /etc/modprobe.d/ will be parsed so a modprobe.conf file in this directory would work, but not in your home directory - I could be proved wrong though!]


Utar

---

