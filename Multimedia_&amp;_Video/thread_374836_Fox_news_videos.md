---
title: "Fox news videos"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by trents on 2007-03-03
Has anyone had any success playing the embeded videos on the foxnews.com web site. I can play the ones on CNN but I only get audio on FoxNews. I've got all the pugins and codecs installed that automtix and easy ubuntu offer.

Steve

---

### Post by ssavelan on 2007-03-03
HAHAHA, right to the *sound* of a Microsoft commercial with nice acoustic guitar music, no video.

I thought that I had remembered that, ESPN, MSNBC, Democracy Now, BBC, CNN, youtube, myspace....

and not FOX news, what a tragedy, LOL!!!

I guess I'll have to go back to Winduhs.... so I can get doubly dumbed-down.

Sorry, if I offend...  I hope that we can fix this so everybody who wants to watch FOX from ubuntu can.

---

### Post by david_2001 on 2007-03-03
I haven't tried it but there's a suggested solution [COLOR="SandyBrown"][here]("http://forums.fedoraforum.org/showpost.php?p=726597&postcount=8")[/COLOR].  The Outfoxed videos on YouTube work without any problem :-)

---

### Post by trents on 2007-03-06
> **ssavelan said:**
> HAHAHA, right to the *sound* of a Microsoft commercial with nice acoustic guitar music, no video.

I thought that I had remembered that, ESPN, MSNBC, Democracy Now, BBC, CNN, youtube, myspace....

and not FOX news, what a tragedy, LOL!!!

I guess I'll have to go back to Winduhs.... so I can get doubly dumbed-down.

Sorry, if I offend...  I hope that we can fix this so everybody who wants to watch FOX from ubuntu can.

What? I'm not sure if this is a commentary on what you think my political views might be or a revelation of what yours are but I do agree it would be nice to get this problem with the Fox News streaming videos fixed.

Thank, David_2001. I'll pursue that when I get a chance. Your response was to the point and helpful.

Steve

---

### Post by sdowney717 on 2007-03-06
[http://vlajbert.blogspot.com/](http://vlajbert.blogspot.com/)

install greasemonkey, then install this script
' Update -- FoxNews Friendly Video'

YOU WILL SEE VIDEO.
I am watching right now

---

### Post by sdowney717 on 2007-03-06
abcnews.com also seems to need a greasemonkey script.

I cant play video there. But I can at cbsnews.

---

### Post by trents on 2007-03-07
> **david_2001 said:**
> I haven't tried it but there's a suggested solution [COLOR="SandyBrown"][here]("http://forums.fedoraforum.org/showpost.php?p=726597&postcount=8")[/COLOR].  The Outfoxed videos on YouTube work without any problem :-)

Okay, I have downloaded and upacked the "mediaplayerconnectivity.0..8.3.xpi" file to a folder on my Desktop called "MediaPlayer". Now how do I install it? I'm pretty green in Linux.

Thanks, Steve

---

### Post by bwallum on 2007-03-08
I've been trying hard to get news video going all day. I cracked it with this:

[https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9](https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9)

Hope it helps!

---

### Post by trents on 2007-03-08
David_2001's link and its solution didn't work for me, even after I figured  out how to install the xpi file. None of the players I choose from the table made a difference. I think I needed to have some file link information to fill in the table and I didn't know how to do that. A few of the player choices had the info file about the file association (or that's what I presume it was)  supplied but others were blank.

Haven't tried the greasemonkey approach yet.

bwallum, are you using Feisty Fawn? It wasn't clear to me what you consider to be the key idea from that string you referenced with your link. A lot of that, such as enabling all the free and nonfree repositories and downloading the codecs is something most of his with this problem have already done. Perhaps you were implying we need to move up to Feisty Fawn as the final piece?

Steve

---

### Post by Detonate on 2007-03-08
The link posted by david_2001 was originally posted by me over on the fedora forum.  Small world.  I have since found that the greasemonkey extension with the fox friendly news script works much better.  It not only lets you watch the video, but it strips out the leading commercial.  Works for me.

---

### Post by trents on 2007-03-08
> **Detonate said:**
> The link posted by david_2001 was originally posted by me over on the fedora forum.  Small world.  I have since found that the greasemonkey extension with the fox friendly news script works much better.  It not only lets you watch the video, but it strips out the leading commercial.  Works for me.

Thanks for the new input, Detonate.  I'll  try it. But isn't it amazing how what works for one doesn't for another even though both are using the same OS?

Steve

---

### Post by Detonate on 2007-03-08
The "Greasemonkey" fix should work.  Question: Are you using the "Adblock" extension for Firefox?  I have found that Adblock can sometimes block videos from opening.  If you need to know how to "whitelist" a site in Adblock, ask me.  Also, the other extension "MediaPlayer Connectivity" allows me to play embedded midi files without installing mozplugger, which if you do a search seems to be the only way to do it. NOT TRUE!  I may write a "how to" on this soon.

---

### Post by trents on 2007-03-08
> **Detonate said:**
> The "Greasemonkey" fix should work.  Question: Are you using the "Adblock" extension for Firefox?  I have found that Adblock can sometimes block videos from opening.  If you need to know how to "whitelist" a site in Adblock, ask me.  Also, the other extension "MediaPlayer Connectivity" allows me to play embedded midi files without installing mozplugger, which if you do a search seems to be the only way to do it. NOT TRUE!  I may write a "how to" on this soon.

"Adblock"? Do you mean "popup blocker"?

Steve

---

### Post by bwallum on 2007-03-08
I'm on Ubuntu 6.10. Sorry to interrupt the flow if you've already done the stuff on my link. I'm new here (1st week) and have managed to get BBC News video working after a day. gstreamer gave me a lot of head scratching, totem-xine-firefox-plugin was much better. It meant downloading xine but it was painless. The link is on the page I posted (scroll down to streamed video) for further stuff including xine. I don't know my base from my apex but the install was fine.  This Ubuntu game is better than Sudoku! Apologies again if I slowed you down.

---

### Post by trents on 2007-03-08
> **sdowney717 said:**
> [http://vlajbert.blogspot.com/](http://vlajbert.blogspot.com/)

install greasemonkey, then install this script
' Update -- FoxNews Friendly Video'

YOU WILL SEE VIDEO.
I am watching right now

You were correct! It works! I note that the description for the "Update -- FoxNews Friendly Video" explains that this script removes the advertising leader from the video. Makes me think that Detonate was on to something when he suggested turning of "Adblocker".

One more crossed off on my list of "Can't do in Linux" issues. Got palm hotsync to work the other evening. Now, I need to figure out TV capture/recording.

Steve

---

### Post by Detonate on 2007-03-08
> **trents said:**
> "Adblock"? Do you mean "popup blocker"?

Steve

No, Popup Blocker is built into Firefox, Adblocker is an extension you can install, that is much more powerful than Popup blocker.

---

### Post by bwallum on 2007-03-10
I am pretty sure the problem lives with the way Flash is implemented in Debian. I have been round the houses with this and currently have a thread drilling into the problem. Whilst not exactly the same scenario, Flash is the common factor. This is the thread (I'm new so hope I have got the referencing correct) [http://www.ubuntuforums.org/showthread.php?t=380247](http://www.ubuntuforums.org/showthread.php?t=380247)

If you have made progress with FOXnews please let me know.

Regards, Bob

---

### Post by shane2peru on 2007-06-14
> **sdowney717 said:**
> [http://vlajbert.blogspot.com/](http://vlajbert.blogspot.com/)

install greasemonkey, then install this script
' Update -- FoxNews Friendly Video'

YOU WILL SEE VIDEO.
I am watching right now

HELLLLLP!!!  Ok, I know I have done this before, and don't understand why it is not working now!!!  I have a fresh install of Kubuntu, and installed greasemonkey, then downloaded that script.  I then dragged it and dropped it on the greasemonkey window inside of firefox tools.  It installed, I think.  I shut down and logged out and everything, and nothing!!!  I get voice but no video on fox news.  I'm using 7.04, and this is annoying.  I have done this in Gnome without a problem.  If anyone knows what I'm doing wrong and can help point it out I would greatly appreciate it.  Thanks.

Shane

---

### Post by Detonate on 2007-06-14
Is the Greasemonkey Icon showing at the bottom right of your FF page?  Right click on it and open "Manage User Scripts" to be sure the FoxNews Friendly Video is installed.

I usually install it by clicking on "Install this Script" in the upper right corner of this page.

[http://userscripts.org/scripts/show/1371](http://userscripts.org/scripts/show/1371)

---

### Post by shane2peru on 2007-06-15
> **Detonate said:**
> Is the Greasemonkey Icon showing at the bottom right of your FF page?  Right click on it and open "Manage User Scripts" to be sure the FoxNews Friendly Video is installed.

I usually install it by clicking on "Install this Script" in the upper right corner of this page.

[http://userscripts.org/scripts/show/1371](http://userscripts.org/scripts/show/1371)

**THANK YOU!!!!**  That did the trick.  I did have Grease monkey installed and running, had problems getting the script installed into Grease monkey.  Thanks!
:popcorn:

Shane

---

### Post by BLTicklemonster on 2007-09-11
> **trents said:**
> What? I'm not sure if this is a commentary on what you think my political views might be or a revelation of what yours are but I do agree it would be nice to get this problem with the Fox News streaming videos fixed.

Thank, David_2001. I'll pursue that when I get a chance. Your response was to the point and helpful.

Steve

Get used to that here. The place is like /. , crawling with LIEberals.

---

### Post by BLTicklemonster on 2007-09-11
> **shane2peru said:**
> **THANK YOU!!!!**  That did the trick.  I did have Grease monkey installed and running, had problems getting the script installed into Grease monkey.  Thanks!
:popcorn:

Shane

Wow. that totally shut it down. Now I have no audio, just a white box.

---

### Post by MarcG on 2007-10-13
I've got greasemonkey and fox friendly script installed and enable, but I'm still in the same situation. Video doesn't work, but sound does. The Fox Friendly script gets rid of the commercials nicely, but that's it.

Anything else I can check?

---

### Post by MarcG on 2007-10-13
Forgot to mention - This is a new install of 7.04, flashplugin is installed, and videos seem to work OK  everywhere else I've tried.

---

### Post by shane2peru on 2007-10-13
> **MarcG said:**
> Forgot to mention - This is a new install of 7.04, flashplugin is installed, and videos seem to work OK  everywhere else I've tried.

I'm pretty sure that the greasemonkey and Foxnews thing is in the repos of 7.04.  Backup you ~/.mozilla folder just in case it doesn't work you can restore it.  Then install it from the repos and give it a try.

Shane

---

### Post by MarcG on 2007-10-13
> **shane2peru said:**
> I'm pretty sure that the greasemonkey and Foxnews thing is in the repos of 7.04.  Backup you ~/.mozilla folder just in case it doesn't work you can restore it.  Then install it from the repos and give it a try.


Thanks, Shane. I tried that, but no dice.

--Marc

---

### Post by shane2peru on 2007-10-14
> **MarcG said:**
> Thanks, Shane. I tried that, but no dice.

--Marc

Marc,

I hate to see someone go without Fox news.  Here is what we are going to try.  I'm going to give you all the commands in case you don't know them, save you a post.  
1st backup Firefox
```
cp .mozilla .mozilla-backup
```
Next we are going to remove this the Firefox folder and start all over.
```
rm -frv .mozilla 
```
Now open up Firefox again, and try and install the script just to see if you can get it working from scratch.  Or install them from the repos, I don't remember the name of them or I would give you the commands and I'm using Gutsy now.  If it works we will figure out how to move your bookmarks over if you have any.  Also you will have to re-install any other add-ons you had.  Small price to pay to watch Fox news.  Those are of course in the terminal that you are going to use those commands.  Let me know if this works.

Shane

---

### Post by MarcG on 2007-10-16
Thanks, Shane, but I don't think that Foxnews videos are really that important to me :) It was easy enough to install Greasemonkey and then the Friendly Fox script. And I do think that the script is at least partially working, as I hear the audio part of the video's news part, but not the commercial part. However, I don't want to play that much with all my settings just to watch the occasional Fox video that might catch my attention.

--Marc

---

### Post by shane2peru on 2007-10-16
> **MarcG said:**
> Thanks, Shane, but I don't think that Foxnews videos are really that important to me :) It was easy enough to install Greasemonkey and then the Friendly Fox script. And I do think that the script is at least partially working, as I hear the audio part of the video's news part, but not the commercial part. However, I don't want to play that much with all my settings just to watch the occasional Fox video that might catch my attention.

--Marc

Understood.  I live outside of the US and my only US news source is via the web, and Fox News mostly.  

Shane

---

### Post by JaceMan on 2007-10-23
> **sdowney717 said:**
> [http://vlajbert.blogspot.com/](http://vlajbert.blogspot.com/)

install greasemonkey, then install this script
' Update -- FoxNews Friendly Video'

YOU WILL SEE VIDEO.
I am watching right now

Hooray for Greasemonkey!  That's the ticket.

---

