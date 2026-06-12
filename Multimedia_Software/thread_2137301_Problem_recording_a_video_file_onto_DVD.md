---
title: "Problem recording a video file onto DVD"
date: 2013-04-20
forum: Multimedia Software
---

### Post by harfin on 2013-04-20
Hi
I have recorded on my PVR a film from TV. 
  
The three files created by the PVR have the file-name moveiename.ts, moveiename.nts, moveiename.hmt, 
 The 1st file seems to be the one that is the movie, as it's size is 2.6Gb; the second is 5.8Mb nd then third is 4.9Kb
  
When the moveiename.ts file is opened with VLC it plays correctly on my ubuntu PC (Precise Pangolin 12.04, 64bit)

I wish to transfer the file onto a DVD so that it can be watched on a standalone DVD player, a Toshiba DVD Recorder/Player hooked up to a tv. 
 
The moveiename.ts will not play on either using either a Toshiba or a Sanyo player.

I tried using VLC to convert the movie to MP3 but [I]&#8203; get the error 
[/I][COLOR=#FF0000][FONT=arial][/FONT][/COLOR][INDENT][COLOR=#FF0000][FONT=arial]Streaming / Transcoding failed:[/FONT][/COLOR][/INDENT]
[FONT=arial]It seems your FFMPEG (libavcodec) installation lacks the following encoder:[/FONT]
[FONT=arial]MS MPEG-4 Video v1.[/FONT]
[FONT=arial]If you don't know how to fix this, ask for support from your distribution.[/FONT]

Anyone any suggestions or ideas?

I am a novice at this :-)
Alan

---

### Post by The Spectre on 2013-04-20
You might want to give DeVeDe a try.

And if DeVeDe doesn't work with that file format you might try using Handbrake to Transcode it to an MP4 format first.

---

### Post by harfin on 2013-04-20
> **The Spectre said:**
> You might want to give DeVeDe a try.

And if DeVeDe doesn't work with that file format you might try using Handbrake to Transcode it to an MP4 format first.

Thanks for quick response.

Looks like the transcode is needed.  Cannot sight 'handbrake' on Ubuntuu. Software Centre though.  Do I download a it via the link on Handbrake's site?

Alan

---

### Post by The Spectre on 2013-04-20
This is where you can get the info to add the PPA for Handbrake...

[https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)

---

### Post by harfin on 2013-04-21
> **The Spectre said:**
> This is where you can get the info to add the PPA for Handbrake...

[https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)

Alas I get an error message on the terminal, "Cannot access PPA". I typed in precisely what it said to key from the page you directed me to.  The last bit of the error message said "please check your internet connection". Nothing wrong with my connection, it's working fine.
Alan

---

### Post by harfin on 2013-04-21
My entry - sudo add-apt--repository ppa:stebbins/handbrake-releasess
Error : *"Cannot access PPA ([https://launchpad.net/api/1.0/-stebbings/+archive/handbrake-releases](https://launchpad.net/api/1.0/-stebbings/+archive/handbrake-releases)) to get PPA information, please check your internet connection"*

---

### Post by The Spectre on 2013-04-21
> **harfin said:**
> My entry - sudo add-apt--repository ppa:stebbins/handbrake-releasess
Error : *"Cannot access PPA ([https://launchpad.net/api/1.0/-stebbings/+archive/handbrake-releases](https://launchpad.net/api/1.0/-stebbings/+archive/handbrake-releases)) to get PPA information, please check your internet connection"*

It looks like you had a couple of typos in your command.

Just copy and past this into Terminal...
```
sudo add-apt-repository ppa:stebbins/handbrake-releases
```

To complete the installation of Handbrake...
```
sudo apt-get update

sudo apt-get install handbrake-gtk
```

---

### Post by harfin on 2013-04-21
[COLOR=#000000]It looks like you had a couple of typos in your command. :-(
Thanks, your eyesights obviously far better than mine!
So, how do I get the actual handbrake software?
Alan[/COLOR]

---

### Post by harfin on 2013-04-21
I entered the command you gave and the system did it's thing, successfully it seemed.Do I now have to enter a command to get the software?
Alan

---

### Post by The Spectre on 2013-04-21
> **harfin said:**
> I entered the command you gave and the system did it's thing, successfully it seemed.Do I now have to enter a command to get the software?
Alan

To complete the installation of Handbrake...
```
sudo apt-get update

sudo apt-get install handbrake-gtk
```[COLOR=#000000]
After that you should be good to go...
[/COLOR][ATTACH=CONFIG]241609[/ATTACH]

---

### Post by harfin on 2013-04-21
Thanks for your help.  Got the programme now. Fingers crossed~
Alan

---

### Post by harfin on 2013-04-21
Well Spectre, that certainly worked!

Thank-you so much for all your help, as an Aussie mate said to me once "[I]You're bloods worth bottlin'" :-)

Alan[/I]

---

### Post by The Spectre on 2013-04-21
> **harfin said:**
> Well Spectre, that certainly worked!

Thank-you so much for all your help, as an Aussie mate said to me once "[I]You're bloods worth bottlin'" :-)

Alan[/I]
Glad I could help.:)

These two programs have worked great for me and should serve you well.

---

