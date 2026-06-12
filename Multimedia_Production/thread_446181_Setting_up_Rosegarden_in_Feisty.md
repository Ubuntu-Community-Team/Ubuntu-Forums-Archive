---
title: "Setting up Rosegarden in Feisty"
date: 2007-05-16
forum: Multimedia Production
---

### Post by oliwally on 2007-05-16
I've been looking through forums for a few days now to find a definitive guide on how to set up Rosegarden in Feisty but have not been able to find one.

I'm quite disheartened with how difficult it is to get this thing going and I fear that it's issues like this that keep a lot of users away from Linux. It's just too much mucking around. In Windows it simply just works  - most of the time (don't stone me... :) 

Can anyone point me to a guide on setting up Rosegarden, or perhaps one could be started here? I know there are a lot of post about Rosegarden, but none of them seem to be a step-by-step A-Z guide on how it's done.

Please help!

I've got the low-latency kernel running, I've got a Soundblaster Live card, running Kubuntu 7.04. Rosegarden 4  is installed, but I'm getting no sound. 

What do I do next, what else needs installing?

---

### Post by westli on 2007-05-16
Unfortunately, music production in Linux is still discouragingly fiddly.  Ubuntustudio helps a lot by having everything installed, but there will still be a struggle figuring out how your soundcard is recognized.  Often outputs work and inputs don't because they are set at minimum gain, but there is nothing there telling you that.  

The included music production software seems capable, but unintuitive.  There's a steep learning curve.  

Check out [http://www.rosegardenmusic.com](http://www.rosegardenmusic.com) (which isn't responding at the moment, but is usually okay) and [http://en.wikipedia.org/wiki/Rosegarden](http://en.wikipedia.org/wiki/Rosegarden)

Nothing comes easy.  (Hey!  That's a good idea for a song...)

---

### Post by drosky on 2007-05-16
> **oliwally said:**
> I've been looking through forums for a few days now to find a definitive guide on how to set up Rosegarden in Feisty but have not been able to find one.

I'm quite disheartened with how difficult it is to get this thing going and I fear that it's issues like this that keep a lot of users away from Linux. It's just too much mucking around. In Windows it simply just works  - most of the time (don't stone me... :) 

Can anyone point me to a guide on setting up Rosegarden, or perhaps one could be started here? I know there are a lot of post about Rosegarden, but none of them seem to be a step-by-step A-Z guide on how it's done.

Please help!

I've got the low-latency kernel running, I've got a Soundblaster Live card, running Kubuntu 7.04. Rosegarden 4  is installed, but I'm getting no sound. 

What do I do next, what else needs installing?

It's true that sometimes things are a little more work to set up in Linux, because programmers often don't want to duplicate functionality that already exists elsewhere.

The rosegarden website has a good page on how to get [Rosegarden to produce sound]("http://rosegarden.sourceforge.net/tutorial/en/chapter-2.html"), but here is a quick start that will hopefully work for you:

1. Since you have a SB Live card, you should have hardware MIDI support, but you will need a soundfont to load into the card.  [Hammersound]("http://www.hammersound.net") has many freely downloadable soundfonts.  If your card can handle 32MB soundfonts, the [FantaGM]("http://www.hammersound.com/cgi-bin/soundlink.pl?action=view_download_page;ID=181;SoundFont_Location_Selected=Download;SoundFont_Filename_Selected=http://www.jchyun.com/download/sbk/fgm32v15/FantaGM32v15.zip") GM soundfont is a good one to start with.

2. The soundfont must be loaded into the card using the "sfxload" program from the "awesfx" package (in the feisty universe repository).  I don't have a SB Live, so I'm not really familiar with using sfxload, but I believe Rosegarden can be configured to automatically run sfxload when it starts to load your soundfont.  Check the preference settings in Rosegarden under sequencer.  To use sfxload manually, check the man page for more info.

3. If your system is configured properly, you should then be able to run Rosegarden and hear notes as you enter them and play back what you have entered.  If it still doesn't work, you may have some issues with proper kernel modules not being loaded, or I may have left something out since I don't have an SB Live - you may want to check the Rosegarden page mentioned above.

EDIT: Correction: I forgot, since this is ALSA-based, you will probably need to use "asfxload", not "sfxload".  Also, there may already be a general midi soundfont located on the driver CD that came with the SB Live.  Look for files that end in ".sf2" or ".SF2".

---

### Post by oliwally on 2007-05-17
Thanks for the replies!

droski, your advice worked! I can hear the midis playing after I used the inbuilt Rosegarden feature to load the soundfont. Thank you so much.

I did what you said (for those reading this and wondering how it worked for me):

I used synaptic to install awesfx.
I took out my SoundBlaster CD and copied a soundfont (.sf2 file) into a directory in my home folder.
Opened up Rosegarden - Settings - Configure Rosegarden... - Sequencer.
Load Soundfont to SoundBlaster card at startup - tick the box.
Path to 'asfxload' or 'sfxload' command - for me that was /usr/bin/asfxload
Soundfont - browse to where I have stored the sound font.

Restart Rosegarden and Bingo!

Thanks folks. I'm sure there will be more questions once I try to record, but this is a great start and somewhat restores my confidence in audio capabilities of Linux.

Edit: I just noticed that out of the two soundfonts I took off the CD, only one works with Rosegarden. So, if you're trying this and it still doesn't work, try a different sound font. Mine was called CT4MGM.SF2 and was 4MB big. The other, non-working one was significantly smaller. Not sure what the other differences may have been.

---

### Post by drosky on 2007-05-17
> **oliwally said:**
> Thanks for the replies!
Edit: I just noticed that out of the two soundfonts I took off the CD, only one works with Rosegarden. So, if you're trying this and it still doesn't work, try a different sound font. Mine was called CT4MGM.SF2 and was 4MB big. The other, non-working one was significantly smaller. Not sure what the other differences may have been.

Glad you got it working.  Make sure to browse Hammersound too.  He hosts links to a large number of both free and non-free soundfonts, and you'll likely find some things you may like better than the default one that came with the card, especially if you want to render your music to a wav or mp3.

---

