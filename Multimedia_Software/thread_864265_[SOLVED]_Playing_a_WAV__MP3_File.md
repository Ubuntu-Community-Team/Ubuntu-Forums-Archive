---
title: "[SOLVED] Playing a WAV / MP3 File"
date: 2008-07-19
forum: Multimedia Software
---

### Post by Jesdisciple on 2008-07-19
I've installed BMPx so I can hopefully play [http://www.bentbay.dk/stuck_on_you.wav](http://www.bentbay.dk/stuck_on_you.wav) (which, Firefox tells me, "requires an MPEG-1 Layer 3 (MP3) decoder plugin which is not installed").  But, whenever I tell BMPx to play said file, it crashes.  :confused:

Please help... again.

---

### Post by cozmicharlie on 2008-07-19
You need to install the codecs.  See this thread for help [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683).

I was able to play the file in Firefox using mplayer so once you get all the proper codecs installed and install the mplayer plug-in for Firefox you should be fine.  Post back if you have any problems or need help.

---

### Post by Jesdisciple on 2008-07-19
My terminal window is stuck "Configuring sun-java6-bin" with the "Operating System Distributor License for Java version 1.1 (DLJ)" displaying.  I see "<Ok>" at the bottom, but clicking it does nothing.  I also tried the **less** commands like q, h, etc., but with no luck.  How do I get out?

EDIT:  Sorry, I got it.  Use the cursor keys to navigate to the 'buttons' and press Enter.

---

### Post by Jesdisciple on 2008-07-19
Update: Okay, I've gone through Part 2, Option 1.  I'm not sure what part of the linked Apple.com page I'm supposed to be paying attention to, but the WAV I linked to above says it's playing while I don't hear anything.

---

### Post by cozmicharlie on 2008-07-19
The link to apple.com is simply for testing to make sure you can play the quicktime movies.  Just try and play any of the movie trailers - you should be able to double click and it should bring up an option for small, medium, large etc.  Select one (small or medium) and it should play.

Since the wave is playing I assume it is playing in mplayer.  There is a volume button on the lower right so make sure the sound is turned on and the volume up.  Also, did you do this step?

"Please Note: New users of Ubuntu or MPlayer should open the main MPlayer application after installing it for the first time, this will then cause it to create it's default folder in your home directory. Also, please navigate to Preferences > Audio in MPlayer, and and make sure the "Enable Software Mixer" option is ticked."

What they mean is to open mplayer from the menu - applications>sound & video.  In mplayer go to the menu>preferences>audio in mplayer.

You may also need to reboot after you do all this.

---

### Post by Jesdisciple on 2008-07-19
Yes, my volume is up, and I have rebooted.  Nothing has changed.

I opened and closed Mplayer just now, then clicked a trailer image.  When no video started, I followed the instructions to update Quicktime before realizing that I had another link to click.

I chose the Traitor trailers, but all I see is the green rating splashscreen ("This PREVIEW has been approved...").  If I scroll, the video scrolls under the page - so the bottom gets hidden by other page elements and the top gets replaced by a blue background...

---

### Post by cozmicharlie on 2008-07-20
OK - lets narrow this down and see if it is an issue with mplayer in general or just the plug in.  Can you play a regular dvd movie using mplayer and get a picture and sound?  

Also, I am assuming you are in Hardy - is that correct?  

If the dvd plays fine then the problem is in the plug in.  In some cases Flash causes problems.  If you can play the dvd fine, try this and see if it helps. Cut and paste the following.

```
sudo apt-get purge flashplugin-nonfree gnash gnash-common libflash-mozplugin libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree  
```

---

### Post by Jesdisciple on 2008-07-20
Erm, I don't have a DVD readily available...  My parents have several, but they're on vacation and their house is out of my practical reach.  Do I need to wait 'til they return to continue testing?

Yes; I initially installed Gutsy but recently upgraded to Hardy.

---

### Post by cozmicharlie on 2008-07-20
No you don't need to wait.  Go ahead and make the changes - copy and paste the following command in a terminal.

```
sudo apt-get purge flashplugin-nonfree gnash gnash-common libflash-mozplugin libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```

You can also test your sound by going to system>preferences>sound.  Let me know the results from the test.

---

### Post by Jesdisciple on 2008-07-20
```
E: Couldn't find package nspluginwrapper
```Other than that, the command went fine.

And I know my sound works; I use [Pandora]("http://www.pandora.com/") frequently.  :)

---

### Post by cozmicharlie on 2008-07-20
Since all you are doing is purging nspluginwrapper the message can be ignored.  Did you try and play the trailers again?  Did it help?

If you go to the site [http://www.bentbay.dk/stuck_on_you.wav](http://www.bentbay.dk/stuck_on_you.wav) to play this and mplayer comes up - right click and go to configure.  I have attached a screenshot of what it looks like when I do this.  Does yours look the same?  Do you have all the checks that I have?

---

### Post by Jesdisciple on 2008-07-20
Well, there's been a slight change - although I'm not sure if it's good, bad, or neutral. Trailer 1 stops at **Cache fill: 100.0%** and the video remains gray; Trailer 2 still scrolls under the page.

A similar change has occurred at stuck_on_you.wav: whereas I did see a black background with a gray "play" button, it's now completely gray except for the control bar that still says "Playing".

---

### Post by cozmicharlie on 2008-07-20
OK - we may have to start over again but lets try one more thing first. 
[INDENT]Copy the url ([http://www.bentbay.dk/stuck_on_you.wav](http://www.bentbay.dk/stuck_on_you.wav)).
Open mplayer applications>sound and video>mplayer
Right click on the mplayer (anywhere within mplayer) to bring up the menu.
Go to open>play url and paste the url and hit OK
[/INDENT]

Let me know if it plays when you do this

---

### Post by Jesdisciple on 2008-07-20
No, I just get a dialog with title "Error!" and no content...  That's got to be least descriptive error I've ever seen.  And it won't close. :\  EDIT: And MPlayer has 10 processes open...??  EDIT2: And I ended all of them but one changed its status to "Uninterruptible" before (supposedly) ending and the undead player is still open.

EDIT3: I just rebooted my computer to get rid of the player, then opened Firefox.  It opened my old tabs like it's supposed to, and I'm now listening to the WAV file.  I'll make a new post after testing everything else.

---

### Post by cozmicharlie on 2008-07-20
You do need the nspluginwrapper so lets install it.  Run the following commands in the terminal.

$ sudo apt-get remove --purge flashplugin-nonfree
$ wget -c [http://launchpadlibrarian.net/16150887/nspluginwrapper_1.1.0-0conn2_i386.deb](http://launchpadlibrarian.net/16150887/nspluginwrapper_1.1.0-0conn2_i386.deb)
$ sudo dpkg -i nspluginwrapper_1.1.0-0conn2_i386.deb
$ sudo apt-get install flashplugin-nonfree libflashsupport
$ sudo apt-get remove --purge totem-mozilla
$ sudo apt-get remove --purge mozilla-plugin-vlc
$ sudo apt-get remove --purge gnome-mplayer gecko-mediaplayer && sudo apt-get install gnome-mplayer gecko-mediaplayer

Reboot and restart Firefox and check it.

---

### Post by Jesdisciple on 2008-07-20
[EDIT]Woops, didn't see that.  Sec...[/EDIT]

This will be kinda long; maybe I should make a few bug reports?  Everything works fine with a few small ticks:[list]
[*]Before playing the WAV, standalone MPlayer gives an error "Couldn't resolve name for AF_INET6: www.bentbay.dk".
[*]Before playing [_the first Traitor trailer (direct link)_]("http://movies.apple.com/movies/independent/traitor/traitor-tlr1-h.ref.mov") for the first time, standalone MPlayer gave an error about not finding "the video_out (-vo)".  Now it just gives a DNS error as with the WAV.
[*]Two consecutive times that I tried to play the first trailer in the browser, I had the WAV open in another tab.  The video copied and resized the gray background *and the snippet of text telling where the plugin put the WAV in **/tmp*** from the WAV.  I closed the WAV and the background stayed.  I changed windows (or maybe just tabs) and it worked.
[*]The videos still scroll under the page, but then they correct themselves.
[/list]

---

### Post by cozmicharlie on 2008-07-20
> **Jesdisciple said:**
> [EDIT]Woops, didn't see that.  Sec...[/EDIT]

[list]
[*]Before playing the WAV, standalone MPlayer gives an error "Couldn't resolve name for AF_INET6: www.bentbay.dk".
[*]Before playing [_the first Traitor trailer (direct link)_]("http://movies.apple.com/movies/independent/traitor/traitor-tlr1-h.ref.mov") for the first time, standalone MPlayer gave an error about not finding "the video_out (-vo)".  Now it just gives a DNS error as with the WAV.
[*]Two consecutive times that I tried to play the first trailer in the browser, I had the WAV open in another tab.  The video copied and resized the gray background *and the snippet of text telling where the plugin put the WAV in **/tmp*** from the WAV.  I closed the WAV and the background stayed.  I changed windows (or maybe just tabs) and it worked.
[*]The videos still scroll under the page, but then they correct themselves.
[/list]

"Before playing the WAV, standalone MPlayer gives an error "Couldn't resolve name for AF_INET6: www.bentbay.dk"."
Yes - this happens to me also.  All you need to do is press OK and the message goes away and it plays the audio.

You may have to play with your preferences - under audio and video it gives various options (for example ALSA or OSS for audio).  You may have to select different options and see which works.

Problem in Ubuntu is you can't have multiple audio sources open and playing.  I don't think tis has been fixed yet.

Did you follow the steps in my last post.  If not it may fix some of these.  The nspluginwrapper should help to automatically correct some of these issues.

So it sounds like you have it working for the most part - is that correct?  I hope so.

---

### Post by Jesdisciple on 2008-07-20
I didn't see #2a this time around; it may have been resolved or it may just not show up every first time.
#3 was partly my mistake; it was a different filename displayed in the video than in the WAV.  However, it's only displayed in a video when another sound source is playing, and the video (including the visual) never starts in these cases...  Not that this is probably anything new to you, but I'm correcting myself.
#1 & 2b and #4 persist, but they're very minor and #4 is justifiable.

Yes, it's working; thanks much!

---

### Post by cozmicharlie on 2008-07-20
Great to hear - please mark the thread as solved

Enjoy

---

