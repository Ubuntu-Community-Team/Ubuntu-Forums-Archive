---
title: "Flash video works but almost nothing else"
date: 2009-11-11
forum: Multimedia Software
---

### Post by benenglish on 2009-11-11
In the wake of a HD failure, I threw a Hardy LTS desktop install from the alternate install CD onto a piece of server hardware I had.  It has no sound card and only integrated Intel graphics (output via VGA that won't drive my 24" LCD panel to full res) so it probably won't make a good long-term machine but I'm making do.

The graphics seemed fine at first.  Embedded flash stuff, like from youtube, plays fine.  In fact, Flash sites look pretty darn good, playing quite smoothly.

However, I can't get any movie files to display.  Whenever I try to play an AVI, MPG, or WMV file, I get a black screen.

Here's an oddity, though:  *something* on the system can see into these files.  In a thumbnail view of a file folder, the content is displayed.  But no program seems able to simply play back the video.

Here are the errors I get from the players I have installed:

Player 1:  Movie Player (Gstreamer)
Error message:  > An error occurred  Failed to connect stream: Invalid argument
What I see:  The window section where the graphics should display is black.

Player 2:  MPlayer Movie Player
Error message:  > Fatal error!  MPlayer interrupted by signal 13 in module:play_audio
(How do I turn off smilies?  The line above should have had a colon and a small letter "p", not a smilie.)
What I see:  The window where the graphics should appear is black.

Player 3:  VLC Media Player
Error message:  none.  
What I see:  The progress slider at the bottom of the window moves normally, as if the movie were playing, but the window where the graphics should appear is black.

I've searched the forum and googled for text strings in the errors and still don't find anything specifically on point.  Can anybody give me some advice as to how I should go about diagnosing and fixing this situation?

TIA for any help or insight,

Ben

---

### Post by acho on 2009-11-12
I think u must re-installing gstreamer package... I have same problem with u, but after do re-installing... it's solve today ;)

first u must remove all the gstreamer installed...
Application --> Add/Remove..

then u can play it.. when u open the media file. like MP3, MOV, FLV.... then the player ask the codec... then download it, at that time....cheers!!!

if u can't play flash file like SWF... try to re-installing then i try to install adobe flash player 10 from third party software.... now it's fine to play youtube video in my mozilla browser....

---

### Post by benenglish on 2009-11-14
> **acho said:**
> I think u must re-installing gstreamer packageI appreciate the suggestion, but a full uninstall and reinstall of all programs used to play videos results in...exactly the same situation.

---

### Post by HappyFeet on 2009-11-14
> **benenglish said:**
> I appreciate the suggestion, but a full uninstall and reinstall of all programs used to play videos results in...exactly the same situation.

Unless you do:
```
sudo apt-get clean && sudo apt-get autoremove
```, reinstalling does nothing. Do that command after uninstalling/before reinstalling. I'm not saying it will work, but it is good practice in most cases.

---

### Post by benenglish on 2009-11-16
> **HappyFeet said:**
> Unless you do:
```
sudo apt-get clean && sudo apt-get autoremove
```, reinstalling does nothing. Do that command after uninstalling/before reinstalling. 
OK, got it.

I asked synaptic package manager to completely remove everything with gstreamer in the name.  It asked to also uninstall many related items and I OK'd it all. 

After the uninstalls, I did Applications>Accessories>Terminal so that I could input the line you provided.

And now I have no terminal (that's launchable from the GUI, anyway).  

And now I have no associations between menu'd locations and my home folder.  

And who knows what else I've broken.

Based on all the research I've done (which is far more than I wanted to), it appears that gstreamer absolutely requires some sort of sound device be present if it's going to work.  It won't just output the video stream to the video device; if there's audio present, it wants to see an audio device.  In every case where people have documented solutions to getting video to play, getting the sound to work was a necessary precursor.  Since this hardware has no provision of any kind for sound, I've concluded that I'll never get video players working on it.

This hardware was just intended to be a stop-gap measure until I got a new desktop machine.  In the last day or two I've managed to acquire a new box to use for desktop work.  So before I screw up anything else and while I still have my files accessible to me, I'm going to copy them off and just rebuild this hardware as the server it was originally intended to be.

Thanks to all for the help.

---

