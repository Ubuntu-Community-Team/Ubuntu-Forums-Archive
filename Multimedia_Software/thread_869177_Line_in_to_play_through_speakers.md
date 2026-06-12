---
title: "Line in to play through speakers?"
date: 2008-07-24
forum: Multimedia Software
---

### Post by zaybertamer on 2008-07-24
Hi, first I did do some exploring in all the sound options and such, and also did search for a while to see if I could find an answer there, but I didn't.

I want to know if I can take the audio that is going into the line in on my sound card and play it immediately, as I can do this in windows easily.

I'm using ubuntu 8.04, & I have a Razer Barracuda AC-1, which shows up as C-Media CMI8788 here in linux. The audio source would be my xbox 360. I have sound working for everything else, I just can't get the line in to play.

Can anyone help me with this? Thanks!

---

### Post by immoral giant on 2008-08-17
I'm in the same situation but using X-Fi through OSS.

---

### Post by zigga15 on 2009-04-24
BUMP - I need help with this as well - does anyone have any suggestions.

ossxmix does not have anything to allow line in to play.

---

### Post by Luffer on 2009-05-16
Add my name to the list, can't get line-in to work at all. I use it for my xbox 360 sound, playing it through PC speakers.

Been searching for ages, been digging through all the sound options, but nothing :-(

---

### Post by yourmother on 2009-06-19
I got this to work, but now I forgot exactly what I did to make it work. Here is a best guess. I don't really want to make my computer to go back to not working, so here's to a faulty memory!

Right click on volume control in taskbar (the speaker icon). Select "open volume control." Then click on "preferences." In the volume control preferences, you should have something called "Line-in Capture" listed, activate that checkbox. Mess around with that. (I thought this is what got it to work on my computer, but now I toggle the checkbox and nothing changes, i.e., the sound doesn't kill). See if anything changes... if that isn't it try the following: activate "Line-in Mode" and make sure the "options" tab lists it as "Line-in" and not "Rear output"

---

### Post by rybl on 2009-07-22
I got this to work.  Here is a screenshot of my configuration.  Make sure you have "analog loopback" checked and not "line in as output".

[IMG]http://imgur.com/HYX47l.png[/IMG]

---

### Post by clancymf on 2009-11-06
Your screenshot is different then my settings.  All I see is 

Headphone : 
IEC958 :
IEC958 Capture :
IEC958 Default PCM :
IEC958 2 : 

Any ideas on how to get your options to appear?

---

### Post by bitrayne on 2010-02-01
I used the command

```
home@home:~$ alsamixer
```to turn up the volume on Line playback. Then pressed M to unmute it. Now I can hear my 360 through my speakers.

---

### Post by browny_amiga on 2010-06-13
Looks like they removed it because it could confuse normal users.

I just found that 

pactl load-module module-loopback

will load the functionality again. 

A little crude, but it worked for me.

Now if somebody could tell me how to specify somewhere that I get the option again in the configuration it would be great.

Cheers

Markus

---

### Post by jbeamz on 2010-07-14
> pactl load-module module-loopback

This is what worked for me thank you! My mixer looks nothing like the other picture.

---

### Post by bobbysmith007 on 2010-09-15
The easiest way I know of:
  * go the terminal
  * Type "alsamixer" and hit enter
  * go right a bunch till you find the input you are looking for ( you may have to go past the end of the screen)
  * make sure you turn the volume up and press m to unmute (if necessary)
  * you should hear your guitar / tv / game console etc (with no lag)

---

### Post by Fadetoz on 2010-11-08
> **bitrayne said:**
> I used the command

```
home@home:~$ alsamixer
```to turn up the volume on Line playback. Then pressed M to unmute it. Now I can hear my 360 through my speakers.

THANKS I missed the fact it was muted there ;)
looked at alsamixer 3 times before I ran across your post.

---

### Post by Lankster on 2011-11-27
in 11.10 alsa mixer no longer works. 
```
alsamixer
```This did help a little.

Couldnt find the other settings?

---

### Post by Lankster on 2011-11-27
> **rybl said:**
> I got this to work.  Here is a screenshot of my configuration.  Make sure you have "analog loopback" checked and not "line in as output".

[IMG]http://imgur.com/HYX47l.png[/IMG]


Have no clue where this is in ubuntu 11.10 ?

---

### Post by p.herewini on 2011-12-01
> **Lankster said:**
> Have no clue where this is in ubuntu 11.10 ?

Lankster, just follow bobbysmith007's instructions:

> **bobbysmith007 said:**
> The easiest way I know of:
  * go the terminal
  * Type "alsamixer" and hit enter
  * go right a bunch till you find the input you are looking for ( you may have to go past the end of the screen)
  * make sure you turn the volume up and press m to unmute (if necessary)
  * you should hear your guitar / tv / game console etc (with no lag)

---

### Post by KiraBlaize on 2012-03-18
I got this to work through Alsamixer, but now I have a lag through my gameconsole. It plays everything twice.

Edit: Never mind. I figured it out. Just lowered my PCM volume.

---

### Post by deekattax on 2012-12-26
> **browny_amiga said:**
> Looks like they removed it because it could confuse normal users.

I just found that 

pactl load-module module-loopback

will load the functionality again. 

A little crude, but it worked for me.

Now if somebody could tell me how to specify somewhere that I get the option again in the configuration it would be great.

Cheers

Markus

That command enabled the functionality with no problem. Supress all mic boost to reduce the noise and you'll get clear sound. Thanks a lot!

---

