---
title: "Comcast SmartZone needs text/html decoder"
date: 2010-05-01
forum: Multimedia Software
---

### Post by RackoWacko on 2010-05-01
Comcast SmartZone Voicemail Playback needs a text/html decoder

Comcast SmartZone Communications Center
[www.comcast.net/smartzone/](www.comcast.net/smartzone/)

Comcast website has a voicemail playback feature.

I am using Firefox 3.6.3
When trying it on Ubuntu 10.04, I get the following messages.

POPUP reads as follows: 
Dialog Box Search for suitable plugin?

Search for suitable plugin?
The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported.

I click on the Search button 

Searching Plugin Packages

RESULT
No packages with the requested plugins found

No packages with the requested plugins found
The requested plugins are:
text/html decoder

---

### Post by MC707 on 2010-05-02
I have this problem too. I try playing a few MP3's, but Instead I get this error.

Anyone got a fix?

---

### Post by cboteros on 2010-05-04
Same issue here, but from Google Chrome under Ubuntu Karmik

I will keep an eye on this treat for some solution, thank you in advanced.

---

### Post by BF79 on 2010-05-04
i called comcast tec today  and i think when i told the girl i was using  Ubuntu   her head exploded  got all the way to a manager before i got someone who even knew what a linux OS was  
but i told them that there voicemail doesn't work with it and they should really try to make it work cuz alot of new machines will be coming with it pre-installed on them  
'then they sent me to some engineer person  who actually seemed to care just a little about my complaint  and said he would email me in a day or two  with a answer  to if they can adjust something on there end and make it compatible  
personally  i have a better chance of being hit by a falling star in tonights meteor shower than ever getting a straight answer from them  
but in the event that i do get anything worth posting i will share with all us sorry comcast customers ;)

---

### Post by mcendoo on 2010-05-10
I had the same/similar problem.  I had no problem playing audio files (.wma, .mp3).  When trying to play comcast voice mails I could download them and play them in MoviePlayer, but if I tried to play them within SmartZone I got the search for text/html codec fruitless exercise.  I am currently running Lucid, but had the voicemails working within the Smartzone sometime in the past.  I started by installing gecko-mediaplayer using Synaptic and, voile!, I could play the voicemails with SmartZone.  I don't have the time at the moment to figure out exactly how this works but I thought I would post this and see if it works for anybody else.

---

### Post by blazewon22 on 2010-05-15
I installed the Gecko-Mediaplayer and it worked perfectly!

Thanks!

---

### Post by phubert28 on 2010-06-03
I did as well, thanks!

Of course it requires a restart of Firefox!

I'm emailing Comcast with the results.

---

### Post by ramblinche81 on 2010-06-03
I have the opposite problem...my laptop running Vista cannot play a comcast voicemail, I can only download to media player.....I get a message...the requested file could not be located......

My desktop Karmic plays them with no errors or hangups.

---

### Post by phubert28 on 2010-06-04
Time to replace Vista???? :-)

My WinXP SP3 tanked a few weeks ago... I'd just downloaded 10.4 in 64 and 32 bit and decided to finally take the plunge. Grumbled quite a bit for a week or so, but I've been getting more comfortable.

Linux' parallels to mini and mainframe OSes (I once configured and did systems administration on a small Sun network, a tiny blip in my IT career (retired)) are a little like coming home.

As to your Kharmic ... sounds like it had the right module installed already.

One note:

Comcast responded quickly to my email, assuring me that they would ensure the solution I provided would become available to customers in the future.

It seems we have some customer service wars on between the large providers... I hope it continues!

---

### Post by zbeekman on 2010-07-27
This is great and all, and fixes it for firefox, but google chrome is still broken.  Any one have any thoughts?

Here are all the plugins chrome is using:
[http://uppix.net/b/7/8/37e29f9fbe19ff51f38fdd5ef0e28.png](http://uppix.net/b/7/8/37e29f9fbe19ff51f38fdd5ef0e28.png)

These are what firefox is using:
[http://uppix.net/b/7/8/37e29f9fbe19ff51f38fdd5ef0e28.png](http://uppix.net/b/7/8/37e29f9fbe19ff51f38fdd5ef0e28.png)

Does anyone know exactly which firefox plugin is getting this working?  Also, how do I add that to google chrome?

---

### Post by phubert28 on 2010-10-07
Mine WORKED with the gecko-mediaplayer and now it doesn't (64 bit Ubuntu 10.4, Firefox 3.6.latest, Chromium latest)

Posted email to Comcast... not in a mood to wade thru the phone process just now.

---

### Post by monkeyman_stones on 2011-09-12
While this post is almost a year old I signed up for this forum to try and find a fix for this problem as I am also experiencing it. I'm having the same problem with Ubuntu 10.10 64-bit using Chromium, Firefox and Epiphany. The Comcast voicemail plays on my Nokia N900 (Debian Linux based) so why not on Ubuntu 10.10 64-bit? If my Linux kernel handheld can play it why can't my big box?

My box is also dual boot with Debian 6 64-bit and Comcast voicemail does not play on that distro either.

---

### Post by Trent T on 2012-05-03
I have a work-around while I try to make gecko work--

Right click on the voicemail you want.
Select Download
You have the option to save the resulting .WAV file, or play it with your default media player.

In my case, I play it with Banshee.

---

### Post by hughh on 2012-07-25
> **Trent T said:**
> I have a work-around while I try to make gecko work--

Right click on the voicemail you want.
Select Download
You have the option to save the resulting .WAV file, or play it with your default media player.

In my case, I play it with Banshee.

Ditto, except I find I must occasionally reload the Comcast web page.  BTW, Comcast is not merely bad with non-Windows systems, their overall service for *everything* sucks!

---

