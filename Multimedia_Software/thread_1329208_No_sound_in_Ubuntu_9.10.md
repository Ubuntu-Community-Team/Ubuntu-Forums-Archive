---
title: "No sound in Ubuntu 9.10"
date: 2009-11-17
forum: Multimedia Software
---

### Post by Saew on 2009-11-17
I did a clean install of Ubuntu 9.10 and I'm not getting any sound. When I want to play a song, the playback of the song doesn't even start; it just stays at '0:00'.

I tried searching for solutions in the forums, but nothing has worked so far.

This is my output for step 3 of the sound troubleshoot procedure (found here: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)) : 
[http://pastebin.ca/1674713]("http://pastebin.ca/1674713")

I would appreciate any help :)

---

### Post by VertexPusher on 2009-11-17
What happens when you run speaker-test? Do you hear a sound? If speaker-test returns an error, post its output here.

---

### Post by Saew on 2009-11-17
I don't get any errors, but I don't get any sound either. Any ideas?

---

### Post by alexfish on 2009-11-17
hi the advise per link are correct yet i had to other things to get the pulse audio working correctly , issues with other software ,this became apparent when i installed linux multi media studio , pulse acts as some kind of server ? and permissions are required

this is what i did from a fresh install again !XXX! first 
no downloads or up grades at this time 

I did / goto system /admin / users and groups / ... click to make changes  ..enter your password  click manage groups  in the list i found pulse entries / clicked on each one clicked properties when in checked both boxes user and root ( if more than one user that also)  +  do what was in the link /escaped and did a reboot

sound worked but not 100 % loaded linux mm studio Known as lmms in synaptic
found further issues / 
this was a I do at the time 

whent to synaptic typed in pulse looked down the list and installed basicaly whats in the link + any plugins like vlc pulse / pulse gstreamer etc

however still not 100 % 

in the  applicatins went to sounds and videos clicked on pulseaudio device chooser
 a jack shows up in the top right panel / click on it and a menu list drops down
  like configure local sound server and volume control within thes there are options
 played around until got things working

had to play around with software edit prefs / sound etc 

how ever im now pleased with pulse I think the controls and options for set up are better than the alsa 

ive been doing a post here

[http://ubuntuforums.org/showthread.php?t=1327684](http://ubuntuforums.org/showthread.php?t=1327684)

worth a look and read as it gives an insite at the typical problems / quirks of pulse audio and a couple of screen shots of pulse bits

at the end of the day the bests avises are in the link you have shown

l will post other links as regards to pulse soon they make interesting reading of how good pulse can be / or how bad
 have fun

added links

[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

[http://en.wikipedia.org/wiki/Adobe_Flash#Video_in_web_pages](http://en.wikipedia.org/wiki/Adobe_Flash#Video_in_web_pages)
[http://ubuntuforums.org/showthread.php?t=1305924&highlight=install+home+directory](http://ubuntuforums.org/showthread.php?t=1305924&highlight=install+home+directory)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
...........................................................................
 tutorial quotes

[http://www.unix-tutorials.com/search.php?act=search&term=Enable+Surround+Sound+in+Ubuntu+Linux+%28PulseAudio%29](http://www.unix-tutorials.com/search.php?act=search&term=Enable+Surround+Sound+in+Ubuntu+Linux+%28PulseAudio%29)
..........................................................
added link for enabling speaker channels

[http://www.unix-tutorials.com/go.php?id=4126](http://www.unix-tutorials.com/go.php?id=4126)
[http://mybroadband.co.za/vb/blog.php?b=303](http://mybroadband.co.za/vb/blog.php?b=303)

---

### Post by Bharath on 2009-11-17
When freshly installed I was able to play sound. But after 2/3 reboots... sound died down. Now there is no sound on my laptop. 

lspci:
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

Pls help.

Bharath

---

### Post by Saew on 2009-11-17
@alexfish: Thanks alexfish for your reply. I'm not entirely sure what you're talking about, but I will give it a try.

@Bharath: please don't post in this topic, our problems don't have anything to do with eachother.

@everybody else: Have you got any ideas? :)

---

### Post by alexfish on 2009-11-17
for sound output list
 aplay -l

added   : to find out if the kernel matches system kernel 
modinfo soundcore


try looking at

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by redenex on 2009-11-17
I have the same problem as you did. I found someone posted about reinstalling pulseaudio and it worked for me, but the next reboot, I lost my sound! I guess there should be a plausible solution.:KS

---

### Post by redenex on 2009-11-18
This helped me:  [http://ubuntuforums.org/showpost.php?p=8317477&postcount=1639](http://ubuntuforums.org/showpost.php?p=8317477&postcount=1639)

---

### Post by alexfish on 2009-11-18
> **redenex said:**
> This helped me:  [http://ubuntuforums.org/showpost.php?p=8317477&postcount=1639](http://ubuntuforums.org/showpost.php?p=8317477&postcount=1639)

thanks @ redenex I will pass it on

---

### Post by Saew on 2009-11-19
Thanks guys, but I still have my problem :/

I included a screenshot. You can see the speaker-test running (But I can't hear anything). You can see Rhythmbox kinda _trying_ to play a song but all that happens is that it gets stuck at O:OO.

I don't have a modem, so I can't turn the drivers off.

As you can also see on the screenshot, aplay -l works just like it's supposed to, and in alsamixer you can see everything is unmuted.

Thanks again ;)

---

### Post by VertexPusher on 2009-11-19
It looks like speaker-test got stuck too. There should be continuous messages in the terminal window, but your screenshot shows only the first one.

I would remove PulseAudio and then try the test again.

---

### Post by Saew on 2009-11-19
After executing sudo apt-get remove pulseaudio, I rebooted and then I ran the speaker-test again. This is the output: 

saew@maen:~$ speaker-test 

speaker-test 1.0.20

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib pcm_dmix.c:975:(snd_pcm_dmix_open) unable to create IPC semaphore
Playback open error: -13,Permission denied
ALSA lib pcm_dmix.c:975:(snd_pcm_dmix_open) unable to create IPC semaphore
Playback open error: -13,Permission denied
ALSA lib pcm_dmix.c:975:(snd_pcm_dmix_open) unable to create IPC semaphore
Playback open error: -13,Permission denied
^C
saew@maen:~$

---

### Post by Saew on 2009-11-19
Wait. When I run 'sudo speaker-test' I get the following again:

saew@maen:~$ sudo speaker-test
[sudo] password for saew: 

speaker-test 1.0.20

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 8192
Period size range from 1024 to 1024
Using max buffer size 8192
Periods = 4
was set period_size = 1024
was set buffer_size = 8192
 0 - Front Left

---

### Post by Saew on 2009-11-19
Anyone? :) I haven't gotten my X-Fi Xtreme Audio to work yet, and I don't have any other sound cards at hand.

Thanks,
Saew

---

### Post by Saew on 2009-11-19
It seems my problem might be related to this:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/463829?redirection_url=https%3A%2F%2Fbugs.launchpad.net%2Fubuntu%2F%2Bsource%2Falsa-driver%2F%2Bbug%2F463829&comments=all]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/463829?redirection_url=https%3A%2F%2Fbugs.launchpad.net%2Fubuntu%2F%2Bsource%2Falsa-driver%2F%2Bbug%2F463829&comments=all")

This blows. :)

---

### Post by alexfish on 2009-11-19
hi did you set the  permissions in users and groups / pulse

---

### Post by Saew on 2009-11-19
As in, click on Manage Groups, scroll down to pulse and add myself to that group? 

If so, then yes, I've tried this. Otherwise, what do you mean? :)

Thanks

---

### Post by alexfish on 2009-11-19
> **Saew said:**
> As in, click on Manage Groups, scroll down to pulse and add myself to that group? 

If so, then yes, I've tried this. Otherwise, what do you mean? :)

Thanks

only that on the first speaker test / reads permissions denied ?

---

### Post by Saew on 2009-11-19
Screw it. :) I got rid of my soundcard and put a new one in. 

That "solved" my problem.

Thanks for the help guys :) I guess I have to do with a crappy soundcard for now ;)

---

### Post by alexfish on 2009-11-28
added link for alsa sound / sound cards/  etc worth looking at


[http://www.topology.org/linux/alsa.html](http://www.topology.org/linux/alsa.html)

---

