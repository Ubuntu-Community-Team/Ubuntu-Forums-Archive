---
title: "K3b and Amarok stop working in Intrepid Ibex"
date: 2008-11-07
forum: Multimedia Software
---

### Post by rad_sci_guy on 2008-11-07
I can't get k3b or amarok to work in Ubuntu 8.10.  I can get k3b to run using sudo k3b but it won't let me do anything with the program.

Amarok won't even start flashing a message saying reinstall from source may resolve this problem.

Anyone else having this issue.  It seems Ibex isn't playing nice with kde software.

---

### Post by kayosiii on 2008-11-07
These are both apps that haven't fully been ported to KDE4 - you could be missing some kde 3 libraries - for Amarok you could try the lastest beta of 2.0 instructions on how to install it at [www.kubuntu.org](www.kubuntu.org).... K3B I don't have any better help except that it is working here for me on a default install of 8.10 with all updates applied

---

### Post by jetpeach on 2008-11-08
i don't have this issue, both work fine for me, except that with k3b i can't rip cds right now.

do you have kubuntu-desktop installed? perhaps it got removed while you were configuring other packages? if it's installed and k3b and amarok are installed, i don't see why it shouldn't work (kde3 apps should work fine in kde4 as long as their dependencies are installed)

---

### Post by jetpeach on 2008-11-08
oh, at the terminal you could try reinstalling amarok or k3b - type
sudo apt-get install amarok --reinstall
and the same for k3b
also to be sure kubuntu-desktop is install
sudo apt-get install kubuntu-desktop

---

### Post by rad_sci_guy on 2008-11-22
I'm using the gnome ubuntu, not Kubuntu.  Do I still have to install the Kubuntu-desktop?  I didn't have to do that in previous versions of ubuntu 8.04, 7.10 and 7.04?  why do I have to install the k-desktop now?

As for missing libraries how do I check to see which ones are missing?  is there a list on the K3b and Amarok sites?

I tried the reinstall commands and both programs are still not working.

---

### Post by mc4man on 2008-11-22
I have amarok working fine in 8.10 (ubuntu), no need for kubuntu-desktop.

Did you do a fresh install of 8.10 or upgrade to?

What you might want to do is delete the .kde folder in your home folder and then try starting amarok again.  (enable show 'hidden files' if not already done

While not totally necessary libxine1-ffmpeg should be installed.

---

### Post by rad_sci_guy on 2008-11-25
I did do a clean install of ubuntu 8.10.  I deleted amarok and k3b as well as the .kde folder and reinstalled.

Amarok is working fine now.  K3b starts up normally but it won't let me make and audio cd as it gives me the message:

Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.

I did convert the mp3 and ogg files to wave files and i still get the same message.

anyone have any thoughts on what's going on?

my version of k3b is 1.0.5 using kde 3.5.10

---

### Post by rad_sci_guy on 2008-11-26
Well I tried burning some ogg files to an audio cd and although K3b gave me the same error message as my previous post it I ignored it and continued the the burning phase.  Well it worked.  Funny thing was that it wouldn't burn the wave files to cd.

Very odd.  Must be a bug in K3b.

anyway it's working now.

Thanks to everyone who tried to help me.

---

### Post by wsjunior on 2008-11-26
In order, to get k3b able to burn audio CD's you need to install the libk3b3-extracodecs package.

I'm wondering what do I need to install to make it work with Brasero that freezes when I ask it to burn an audio CD and enter in the mp3 folder to drag the songs to be burnt :/

---

