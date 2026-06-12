---
title: "How can I rip and play DVD-Audio discs?"
date: 2010-06-07
forum: Multimedia Software
---

### Post by finite9 on 2010-06-07
So here's the thing:

I downloaded a DVD-Audio disc as an ISO and it is apparently MPL 24bit/96KHz.

I just bought a new hifi system that supports hires audio discs, and I although my disc player does report that it is playing PPCM 24/96, the AV receiver says it's only going at 48KHz, i.e. downsampled.  I connect the player to the receiver via coax digital.

So, I want to figure out if the disc is *really* 24/96.  Hence, I want to rip the dvd-a to my computer as flac24 files and then query the files in some way to double check they are actually 24/96, then burn these out to backup disc again using dvda-author, where they will definitely be unencrypted, and then check if my receiver can play them at 24/96.  I can already burn flac24 to DVD-A using dvda-author, but do not know how to rip a dvd-a disc.

DVD Audio Explorer and DVDFab for Windows can apparently rip a dvd-a disc according to the DVD-Audio page on Wikipedia but are there any alternatives for Linux/Ubuntu?

I have heard some reports, although they have not been fully confirmed, that you cannot play a copy protected DVD-A at 24/96 when using a digital connection: they will be downsampled to 48KHz.  Is this true?  Does anybody know??

How backwards is that???  That I just bought a system capable of playing hires audio, but it will ONLY work if I output the audio from my DVD player straight to my speakers?  the d/a converter in my dvd player is probably not a patch on the one in my receiver, so _obviously_ one would want to send it digitally to the receiver then have it converted there and then out to the speakers, plus you can see all the signal info if you send digitally to av receiver, which you can't if you send it via analog outputs to the receiver.

How do HiDef formats support this as they output DolbyDigital HD and DTS HD through digital HDMI connectors to the receiver?  How do they stop "pirating digital copies"?  Does it boil down to them having HDCP wheras dvd-a and sacd did not have copy protection in all AV products (in the cable spec.)?

I suppose this means that both DVD-Audio and SACD are both dead as Dodos format-wise, but if I have these discs it would be nice to be able to rip them to the PC.

---

### Post by finite9 on 2010-06-08
Well, I got answers from my hifi dealer...

If you output a DVD-A disc digitally via coax or optical then it will be downsampled to 16bit 48Hz.  This is to stop pirating :)  Thanks for that music industry!

So you have to connect your DVD player with analogue RCA connectors to the receiver but then you do not get information in the receiver about the signal.  Hopefully you will hear the difference, but you've got to know what you're listening for...

So I installed Foobar2000 on a Windows Vista PC with a DVD-A plugin capable of playing back MLP (aka PPCM) audio in the AUDIO_TS section of the DVD-A disc.  I then had to install an ASIO Universal driver... The difference in sound quality was outstanding.  With Foobar, you can get a plugin that does double blind tests, so I compared the stereo downmixed track to the 24/96 track... I may be partly deaf but even I was blown away with the quality difference.  ASIO driver was a _must_.  Using the standard Windows sound driver everything sounds pale in comparison.

Now I need to figure out if this can all be done on Linux, but it seems that there are very very few audiophiles who use Linux... the userspace programs available pale in comparison to the Windows programs.  Foobar has many options but I have only tested this with Rythmbox, which, being Gnome based isn't reknowned for it's feature list... maybe I should try Amarok to compare.

By the way, it is possible to rip a DVD-A disc to WAV files using a program called DVD-A Explorer 2008.  This program, and in fact dvd-a rippers in general, are like gold dust!  Trying to find a working link was nigh on impossible.  After many hours of searching through self-referencing torrent links, I found a file in plain site on the net.  I could even run it through Wine 1.2 to rip my 4.1 channel DVD-A to seperate mono WAV files on hdd.  You've got to be aware about watermarking though: reading through audiophile forums, it seems that even if you rip an encrypted track to disc and burn it back out as FLAC, if it is watermarked this will survive the trascoding and will mute after 30 seconds.  I got the impression that the only way to get around this is to burn the tracks as DVD-Video "films" with no video content and the 24/96 audio as the films audio track.  In this way, the watermarking is not checked by the DVD Player, but then you end up with slightly lower quality audio compared to MLP 24/96.

Now I just have the problem of creating a multichannel FLAC24 file with the 4.1 mono files, and then try to burn them back out to DVD-R using dvda-author: I tried this last night with a stereo mix but dvda-author alpha 2005 just bombed out immediately.  Maybe if I can compile the latest version of dvda-author I will have better luck.

Hope all this information helps out other Linux audiophiles!  Note that if using SACD it's another story!  I cannot find anything to rip an SACD.

btw, you can download DVD-A Explorer 2008 here and run through Wine.  The first 2 links are for beta2, which is what I use, and the third link is beta3.  According to mommymans posts (the author) on Doom9 forums, this was the last beta before he mysteriously quit on the forum:

[http://rapidshare.com/files/111192252/DVDAExplorer2008.04.16.zip.html]("http://rapidshare.com/files/111192252/DVDAExplorer2008.04.16.zip.html")
[http://www.sendspace.com/file/b0vv8b]("http://www.sendspace.com/file/b0vv8b")
[http://thepiratebay.org/torrent/4500112/DVD-Audio_Explorer_2008__Beta_3_%282008.07.21%29]("http://thepiratebay.org/torrent/4500112/DVD-Audio_Explorer_2008__Beta_3_%282008.07.21%29")

I've also attached a compiled version of dvda-author v.9.09 and mkisofs for amd64 platform.  I do have a DEB file for amd64 for the full build, but I did it using checkinstall and it sort of failed to install all dependencies so i'll not post it here.  Drop the patched mkisofs and dvda-author files into /usr/local/bin and make them executable.  t doesn't give you full fuctionality with menus etc, but for plain ripping music and making an iso, this is all you need.  I think you can get an i386 DEB from the sourceforge project page so I'll not post that here.

---

### Post by finite9 on 2010-06-23
I recommend downloading and installing the newer dvda-author 10.06 which fixes some bugs and generally works better.

Shame there are no SACD players for PC.  Impossible to rip SACD at full digital resolution (losslessly) without special hardware that bypass DACs and output to TOSLink, but they are sort of out of my league.

Of course, you can rip a multi channel SACD using analogue RCA outputs, but then it is not a lossless copy.  However... it may only lose some of it's quality; barely noticeable by most people, and each subsequent digital copy made of that initial analogue copy would be the same as the original analogue master...

Honestly, why do they bother with copy protection!?  All it does is cause hassle for the legitimate consumer, because the pirates can STILL make copies and really dont give a rats *** if the initial rip was slightly lower quality.

---

### Post by landroni on 2011-04-23
Thank you so much for all this helpful info! 

I'm still only in my baby steps when it comes to high quality audio, but I was also looking for a way to rip DVD-Audio or DualDisc discs to FLAC on Linux. Unfortunately, the market seems very sparse.

---

### Post by alquery on 2011-08-10
Also, if you want to just play them, you don't need to try (and fail :P) to compile dvda-author (on 64bit at least). VLC will do this just fine.

---

