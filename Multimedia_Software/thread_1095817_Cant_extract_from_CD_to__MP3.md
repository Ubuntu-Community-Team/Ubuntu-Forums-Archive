---
title: "Cant extract from CD to  MP3"
date: 2009-03-14
forum: Multimedia Software
---

### Post by styleruk on 2009-03-14
Arrrrrghhh

What is going on here?  This used to work fine.  Now I can't extract MP3 from a CD!  My solution is at the moment is to fire up vmware, start win XP, run itunes and then extract them!

Ubuntu 8.1
I use Rhythmbox 0.11.6

I put the cd in, it lists all the tracks, I right click 'extract to library' and it does but only in WAV or FLAC.  The options don't allow me to select MP3, it's there and the box marked 'active', is there but I cant select it!
This is driving me nuts.
I guess I can always use the wifes laptop that has itunes on it because I can't use my iphone on ubuntu anyway.  It's just a shame I can't at least extract the MP3s here.

Can anyone point me into the right direction, maybe something somewhere has been 'improved' or removed.

Regards
Si

---

### Post by methodmarvel on 2009-03-14
> **styleruk said:**
> Arrrrrghhh

What is going on here?  This used to work fine.  Now I can't extract MP3 from a CD!  My solution is at the moment is to fire up vmware, start win XP, run itunes and then extract them!

Ubuntu 8.1
I use Rhythmbox 0.11.6

I put the cd in, it lists all the tracks, I right click 'extract to library' and it does but only in WAV or FLAC.  The options don't allow me to select MP3, it's there and the box marked 'active', is there but I cant select it!
This is driving me nuts.
I guess I can always use the wifes laptop that has itunes on it because I can't use my iphone on ubuntu anyway.  It's just a shame I can't at least extract the MP3s here.

Can anyone point me into the right direction, maybe something somewhere has been 'improved' or removed.

Regards
Si
Have you got the "ubuntu-restricted-extras" installed?
Have you tried the "audio CD extractor" program from the sound & video menu?
When did it stop working?
Can you upload a screenshot of "The options don't allow me to select MP3, it's there and the box marked 'active', is there but I cant select it!"?

---

### Post by styleruk on 2009-03-15
> **methodmarvel said:**
> Have you got the "ubuntu-restricted-extras" installed?
Have you tried the "audio CD extractor" program from the sound & video menu?
When did it stop working?
Can you upload a screenshot of "The options don't allow me to select MP3, it's there and the box marked 'active', is there but I cant select it!"?

I don't have the 'restricted extras' installed, I don't even know what they are.
The audio cd extractor uses the same tool to encode mp3 or whatever you choose, only, I have the mp3 option selected but it does not come up as an option.

---

### Post by methodmarvel on 2009-03-17
> **styleruk said:**
> I don't have the 'restricted extras' installed, I don't even know what they are.
The audio cd extractor uses the same tool to encode mp3 or whatever you choose, only, I have the mp3 option selected but it does not come up as an option.

ok - there two ways to get the ubuntu-restricted-extras but the point and click way is:

You can go to the top left menu and click >system >administration >Synaptic package manager

Then in the synaptic package manager in the top left click >edit >search

and in the search box search for ubuntu-restricted-extras

click it's check box and select mark for installation then click apply and exit synaptic

you may need to restart any mp3 related programs eg cd ripper and rhythmbox

this installs support for:
Installing this package will pull in support for M**P3 playback and decoding**,
support for various other audio formats (gstreamer plugins), Microsoft fonts,
Java runtime environment, Flash plugin, **LAME (to create compressed MP3 audio files)**,
and unprotected DVD playback.

---

### Post by 3rdalbum on 2009-03-17
This is a known bug/glitch/unexpected-behaviour/regression. You need to install the "ubuntu-restricted-extras" package from Synaptic Package Manager to get MP3 extraction working.

---

### Post by styleruk on 2009-03-17
I have that installed, I have the generic one installed...
ubuntu-restricted-extras.  Please see a screen shot of what I have installed here...

[www.tyleruk.com](www.tyleruk.com)

I have also put an open office doc there that shows the boxes and options I get in the player.

Si

---

### Post by methodmarvel on 2009-03-17
> **styleruk said:**
> I have that installed, I have the generic one installed...
ubuntu-restricted-extras.  Please see a screen shot of what I have installed here...

[www.tyleruk.com](www.tyleruk.com)

I have also put an open office doc there that shows the boxes and options I get in the player.

Si

You're confused - the pictures in your screenshot are not the same as "ubuntu-restricted-extras" - I'm not sure what those packages are

Follow my rule - "The path of least resistance" aka keep it simple, stupid - I think this will fix it so try it, then try the next easiest fix/search/solution

If my previous explanation wasn't clear I'm sorry but I don't know how to put it any better - trust me and install the package called "ubuntu-restricted-extras"

ubuntu-restricted-extras would not mess you up running kde or xfce

if you wanted I should think you could install ubuntu kubuntu and xubuntu -restricted-extras without errors and they are "meta-packages" and just mark a large collection of packages for installation to make installation simple. The difference is probably environment integration and would not greatly mess with functionality. I'd still suggest ubuntu-restricted-extras though as you choose to use rhythmbox and sound juicer - both gnome apps

just trust me - install "ubuntu-restricted-extras" and ripping cds to mp3 will no longer be a problem

---

### Post by bch36 on 2010-01-06
I had the exact problem as the original poster (styleruk), and the solution by methodmarvel worked for me (i.e. installing the "ubuntu-restricted-extras" package).  

After I did that, extracting an audio CD to mp3 automatically showed up as an option in the preferences for RhythmBox. 

Just wanted to note this so people could tell at a glance that this thread resolved this problem.

---

### Post by devehf on 2010-01-16
I had the Kubuntu-restricted-extras installed and couldn't get Sound Juicer to extract CDs to mp3. Doh! that's because it is a Gnome application, right?

I any case, installing ubuntu-restricted-extras allowed me to select an MP3 option in Sound Juicer's preferences.

Praise Jah!

---

### Post by BubbaBlues on 2010-01-16
Open synaptic and make sure you have "lame" installed.  The best ripper I've tried is asunder cd ripper.  But none of them will encode mp3 for you without lame.

---

