---
title: "Urgently need a DVD ripper that works"
date: 2010-05-11
forum: Multimedia Software
---

### Post by mrapoc on 2010-05-11
I'm on 10.04

Every dvd ripper ive tried so far has failed in one or another.

I have all restricted extras and medibuntu codecs installed.

DVD::Rip either throws an error message or stops ripping somewhere through the process

Handbrake only finds some of the dvd titles

OGM rip gives an "Unknown error"

Acidrip says "mencoder interrupted by user"
:confused:

I have to rip a film for somebodies psp for tomorrow :(

thanks

---

### Post by ron999 on 2010-05-11
Hi
You can use **vobcopy** to copy the vob files of the main movie onto your hard drive as one big vob file.
Then use other software to convert that one vob file into something suitable for the psp.
vobcopy is in the ubuntu repository.

---

### Post by proggy on 2010-05-11
You can also go to Applications>Ubuntu Software Center>Sound & Video , there are lots of tools you can use for ripping ,converting , burning etc,

---

### Post by wkulecz on 2010-05-11
DVD::Rip worked for me on 10.04 with the sample disk I tried to verify my restricted extras setup.  It threw an error on the last VOB file about xxx frames but only yyy frames decoded, but the end of the movie and credits were fine when viewed.

There are a few anti-copy methods not yet defeated on Linux, but since Windows has softare that can rip them, should just be a matter of time ...

I don't re-encode, I just rip our disks to put them on a hard drive so my wife can access them via a media player set top box instead of bothering me to navigate through the assine DVD player menus to play the darn movie!

---

### Post by doas777 on 2010-05-11
if nothing else (and I am reluctant to bring it up) dvddecryptor and dvdfab both work very well in wine.

---

### Post by 2hot6ft2 on 2010-05-11
You could install and use MakeMKV as mentioned in the help pages here:
[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

Installing MakeMKV

Download both of these and save them to your Downloads folder
[MakeMKV Binaries download]("http://www.makemkv.com/download/makemkv_v1.5.5_beta_bin.tar.gz")
[MakeMKV Source download]("http://www.makemkv.com/download/makemkv_v1.5.5_beta_oss.tar.gz")

then
Go to
Places > Downloads
Right click on them both one at a time and select Extract here, then
Open a terminal
Applications > Accessories > Terminal
and run these
```
sudo apt-get install build-essential libc6-dev libssl-dev libgl1-mesa-dev libqt4-dev
```
```
cd ~/Downloads/makemkv_v1.5.5_beta_oss
```
```
make -f makefile.linux
```
it will take a while so wait for it to return to the prompt which will end with
makemkv_v1.5.5_beta_oss$
```
sudo make -f makefile.linux install
```
```
cd ~/Downloads/makemkv_v1.5.5_beta_bin
```
```
make -f makefile.linux
```
That brings up the terms of use. Use the down arrow key to scroll thru them to the bottom and hit the q (Q) hey to return to the terminal. Type in yes and hit Enter to accept them.
```
sudo make -f makefile.linux install
```
All done installing. Now you can start it with
```
makemkv
```
It doesn't create a menu item for it so to create one.
In the top left panel next to Applications
Right click on the Ubuntu Logo and select Edit Menus
In the left side select Sound & Video and click anywhere in the right side.
Click on  

On the right click on New Item
Fill it in like this
Type: Application
Name: MakeMKV
Command: /usr/bin/makemkv
Comment: Can be whatever you want like DVD Ripper

You can click on the launcher picture and pick another one of your choice.
Click OK
All done now it's in the menu in
Applications > Sound & Video > MakeMKV

Once you're done ripping it you could re-encode if you want using Avidemux or another app.

Have fun
:guitar:

---

### Post by mrapoc on 2010-05-11
what do you think is causing all these problems?

anyway of finding out?

---

### Post by dragon99 on 2010-05-12
> **doas777 said:**
> if nothing else (and I am reluctant to bring it up) dvddecryptor and dvdfab both work very well in wine.

Second that. I've found that both dvd shrink & decrypter through Wine work well. I remember seeing a listing of linux alternatives on the wine homepage, some already mentioned on this thread. I think also BD decrypter would work.

dragon

---

### Post by 3rdalbum on 2010-05-12
When using Acidrip, make sure that the title does not have spaces in it.

---

### Post by Linuxforall on 2010-05-12
Handbrake is an excellent DVD ripper, also Bombono, both have their ppa. [www.handbrake.fr](www.handbrake.fr) [www.bombono.org/cgi-bin/wiki/](www.bombono.org/cgi-bin/wiki/)

---

### Post by tobemem on 2010-05-12
>  Every dvd ripper ive tried so far has failed in one or another.>  I have to rip a film for somebodies psp for tomorrow :sad:Do you mean you want your DVD ripped and recoded to a MP4 file with H.264/MPEG-4 AVC video and AAC audio? [ANDREW]("http://tobemem.memebot.com/") can do that, but I'm not sure if your PSP is able to play that file, since there could be restrictions on encoding options, as for iPod and iPhone ([ANDREW]("http://tobemem.memebot.com/") has a compatibility mode for them), I don't know about; [ANDREW]("http://tobemem.memebot.com/") is not in Ubuntu repositories, but all its dependencies are.

---

### Post by BbUiDgZ on 2010-05-12
ffmpeg not work?

---

### Post by mrapoc on 2010-05-12
I think i may have fudged codecs/plugins

Could somebody tell me:

1)how to remove all potential codecs/plugins

2)which ones to reinstall for general multimedia (dvds, mp3, flash etc.)

---

### Post by danootz on 2010-05-12
Is Handbrake working on Lucid Lynx? Last I read, the GUI was busted.

---

### Post by JohnAStebbins on 2010-05-12
> **danootz said:**
> Is Handbrake working on Lucid Lynx? Last I read, the GUI was busted.

You have to use the nightly snapshot builds
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by doas777 on 2010-05-12
> **mrapoc said:**
> I think i may have fudged codecs/plugins

Could somebody tell me:

1)how to remove all potential codecs/plugins

2)which ones to reinstall for general multimedia (dvds, mp3, flash etc.)

I think you are confusing ripping with encoding. which are you interested in at the second?

---

### Post by Objekt on 2010-05-12
Did you try Brasero?  I rarely run into anything it can't rip.  For those exceptions, AnyDVD usually can do the job.

Not sure about transcoding.  I rip to an *.iso image.  Obviously you'll want to drop the resolution by a lot (PSP only being 480x272) for a smaller file.  I have never needed to reformat DVDs for a portable device, so I have no experience in that area.

---

### Post by mrapoc on 2010-05-12
Both ripping and encoding :)

I want to be able to stick a dvd in, rip and encode it to .avi x264 ideally. For backup/storage and viewing on networked devices such as the ps3.

So, if I go back, remove any codec packages and additional programs...what should I be installing to get proper operation?

---

### Post by wired99 on 2010-05-12
"K9copy" works very similar to "Shrink DVD" and you can use "Arista Transcoder" to encode it to whichever format you'd like

---

### Post by MZ250Supa5 on 2010-07-19
This all sounds good, but... I can't get DVD Shrink working through Wine -  Lucid keeps moaning about it not being from a 'safe'source and so is refusing to play ball.  K9Copy just crashes the moment I try and do anything with it.  It's really a pain, as I find DVD 95 impossible to use... the blurb in Software Centre claims that it's 'simple'to use, but I can't seem to get it to select all the files shown... yes, I want the intros and menus etc, but all it seems to want to do is copy individual files and turn them into .iso files individually.  Is there honestly,a simple and *reliable* way to shrink DVDs in Ubuntu? Something a s simple and straightforward as DVD Fab Platinum in Windows? Or do I have to re-install Windows on my other machine for shrinking DVD?

This is a real pain.

---

### Post by VanillaMozilla on 2011-03-24
Just open the DVD and copy the individual VOB files.  Those are video object files.  Some of them don't do much--maybe just a minor menu thing or something, but you can easily get the main video files just by copying.  Some editing programs will not be able to use those directly (don't ask me why), but you can convert them to really, really standard DVD files (VOB) by using ffmpeg.

If it's an encrypted disk, sorry, it's not legal to copy.

I also had some success with AcidRip, although I don't have much experience with it.

---

### Post by dnguyen1963 on 2011-03-25
> **MZ250Supa5 said:**
> This all sounds good, but... I can't get DVD Shrink working through Wine -  Lucid keeps moaning about it not being from a 'safe'source and so is refusing to play ball.  K9Copy just crashes the moment I try and do anything with it.  It's really a pain, as I find DVD 95 impossible to use... the blurb in Software Centre claims that it's 'simple'to use, but I can't seem to get it to select all the files shown... yes, I want the intros and menus etc, but all it seems to want to do is copy individual files and turn them into .iso files individually.  Is there honestly,a simple and *reliable* way to shrink DVDs in Ubuntu? Something a s simple and straightforward as DVD Fab Platinum in Windows? Or do I have to re-install Windows on my other machine for shrinking DVD?

This is a real pain.

Yeah, K9copy crashed on me too when I was using Ubuntu 10.04 LTS.  I am now running ArtisX, which is based on Ubuntu but with a lot of media software included, and K9copy is behaving perfectly.  Use the Wizard function of K9copy to rip your DVD is the best way to go.  Give ArtisX a try.

---

### Post by VanillaMozilla on 2011-03-25
I think your results may vary.  Some people swear by k9copy, but results with it were miserable on my computer.  I think it really, really depends on what media libraries you have installed, and this can vary a LOT, depending on what kinds of files you have tried to read and what codecs you have installed.  Plus, most of this stuff is very poorly debugged because the codecs are too frikken complex and numerous.

It would be really nice if we could get away from all this recommending of programs and figure out what libraries are doing all this crashing.  (Just a suggestion.  I don't have a good handle on this either.)

---

