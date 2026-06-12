---
title: "sound coming from speakers and headphones"
date: 2011-01-14
forum: Multimedia Software
---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2011-01-14
i just installed ubuntu 9.10 via wubi on my toshiba laptop. as far as i can tell the sound card is HDA generic, im not sure if thats right or not, but help is apreciated.

---

### Post by bcbc on 2011-01-15
Try this: [http://newyork.ubuntuforums.org/showpost.php?p=8571901&postcount=6](http://newyork.ubuntuforums.org/showpost.php?p=8571901&postcount=6)

Also how 'bout your toshiba model - might help narrow down the choices

---

### Post by lidex on 2011-01-15
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2011-01-15
bcbc, i looked at that post, but it isnt any help to me, i used that command and it gave me a driver, which i searched for, and it wasnt there.

[http://www.alsa-project.org/db/?f=473d585e3345b40f00632010c5ad13f814177a1d](http://www.alsa-project.org/db/?f=473d585e3345b40f00632010c5ad13f814177a1d)

thats the link that the other user asked for (i cant remember your username, and i dont want to hit back and type this all again, sorry)

---

### Post by bcbc on 2011-01-15
Try this?

[http://www.newyork.ubuntuforums.org/showpost.php?p=10077641&postcount=193](http://www.newyork.ubuntuforums.org/showpost.php?p=10077641&postcount=193)

---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2011-01-15
that didnt work. hey, short of doing this, is there a way of easily muting the speakers all together while im using my headphones?

---

### Post by lidex on 2011-01-16
> **<h1>Mckennie</h1> said:**
> that didnt work. hey, short of doing this, is there a way of easily muting the speakers all together while im using my headphones?

I need you to go into your alsa-base.conf file and remove any lines at the bottom that include snd-hda-intel. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Next add this line:
```
options snd-hda-intel model=thinkpad
```
Save. Close. Reboot.

---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2011-01-16
i did all that, except i didnt look for lines already containing that directive. ill try again and post back

---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2011-01-16
i commented out every line that used that directive and places that one at the bottom of the conf file. still not working

---

### Post by lidex on 2011-01-16
OK. Then try ideapad

---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2011-01-16
that didnt work either

---

### Post by lidex on 2011-01-16
Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2011-01-17
```
E: Couldn't find package linux-alsa-driver-modules-2.6.31-22-generic

```

:/

---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2011-01-17
didnt work

EDIT: oops, double posted by accident, sorry

---

### Post by lidex on 2011-01-18
OK. Let's see where we are now. Run the alsa-info script again please.

---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2011-01-19
[http://www.alsa-project.org/db/?f=f8af839fe22f66c18ba00f9de3ca006b13b1ec19](http://www.alsa-project.org/db/?f=f8af839fe22f66c18ba00f9de3ca006b13b1ec19)

there you go

---

### Post by lidex on 2011-01-19
Very old alsa-drivers. You could upgrade to maverick, or you can update your alsa install. Follow the link in my sig for alsa.

---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2011-01-19
the alsa upgrade worked like charm! cheers! now im one step closer to the perfect ubuntu install

---

### Post by lidex on 2011-01-20
Excellent. <Rubs hands together>
Please mark the thread solved using 'Thread Tools' up top. ;)

---

