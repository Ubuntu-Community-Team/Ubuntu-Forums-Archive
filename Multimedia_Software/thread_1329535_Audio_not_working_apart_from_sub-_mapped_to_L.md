---
title: "Audio not working apart from sub- mapped to L?"
date: 2009-11-17
forum: Multimedia Software
---

### Post by ratykat on 2009-11-17
{This issue is now solved! check the bottom of this post for solution}

Hey there,

I've not used Ubuntu for a long time, and back then it was only a brief affair. 

I decided to dual boot my Windows 7 laptop after seeing my GF's Eee PC laptop running the notebook edition.

Got all the dual boot running fine, sharing media on a 3rd partition etc, all perfect. My only issue is that i cannot seem to get my sound to work.

After a little mess i figured out that it was directing all my sound through my ati HD 4850's HDMI port, i changed this to the internal audio on stereo and I finally got sound.

This issue though is this - the sound I have only comes through the subwoofer at the bottom of my laptop, front l/r and rear l/r dont get any sound. Also, its not stereo pushed through the one speaker, only the left channel.

On windows i had to install a realtek driver to get the speakers closest to the screen working, but I am completely lost on this.

Laptop is a Advent 6555 (MSI GT725)
Sound card is shown as HDA Intel - Realtek ALC1200


I've tried doing this:[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568) and adding : options snd-hda-intel probe_mask=1 to the end of the file, but to no avail.

Been doing this now for about 3 hours with no luck at all...

Any help would be more than welcomed!

Thanks in advance

Leigh

SOLVED!!!!!!

To solve this issue

1. Alt+F2
2. run gksudo nautilus and type in admin password
3. BE CAREFUL! this level of access means you can change nearly everything, meaning anything can be destroyed!
4. Navigate to filesystem/etc/modprobe.b/asla-base.conf
5. scroll to the bottom of that file and add these lines in:
```

options snd-hda-intel probe_mask=1
options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1
options snd-hda-intel model=targa-dig

```
6. save file
7. shut the file browser
8. completely shut down system and restart (this is what I did, you can just reload ALSA, but i wanted to be 100% sure)

and there we go! all working and done!


Credit goes to the guys on this forum and on bug reports found on google which i just pasted in until it worked :)

---

### Post by ratykat on 2009-11-17
Hate to double post/BUMP, but im desperate, its been 5 hours now since ive started and still cannot get the sound working properly :(

leigh

---

### Post by ratykat on 2009-11-18
I do appologise for a second bump, but its a new day and still only 1 speaker :/

---

### Post by markbuntu on 2009-11-18
Thanks for figuring that out, I have added your machine info to the hda-intel database 

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

which is cross linked with the HdaIntelSoundHowTo wiki page. 

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

If anyone knows of any solutions that are not in the database please post them to the database thread or just post a link to where it can be found. I update the OP periodically to save you from wading through all the posts so eventually your post will make it there and help lots of people.

Please mark this thread as solved by using the thread tools above.

---

### Post by ratykat on 2009-11-19
ok put as solved, Im happy that ive contributed, hopfully this will save someone else the amount of time i spent on this!

leigh

---

### Post by AdUki on 2010-10-16
WOW It works for me!
but when i plug in headphones sound comes from headphones AND from internal speakers... i am beginner :) can somebody help me???

i have ubuntu 10.10

---

