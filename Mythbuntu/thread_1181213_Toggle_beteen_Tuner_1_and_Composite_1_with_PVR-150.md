---
title: "Toggle beteen Tuner 1 and Composite 1 with PVR-150"
date: 2009-06-07
forum: Mythbuntu
---

### Post by cleanroom on 2009-06-07
Hi,
   I'm running Mythbuntu 8.04 with a PVR-150 card.  I have analog cable input into the tuner input of the card and my VCR connected to the composite input of the card.  I have been unable to discover a way to switch from tuner view to view input on the composite terminals.  
I'm sure this is simple and probably trivial any help?

Cleanroom

---

### Post by murchball on 2009-06-07
AFAIK there's no way to use the tuner more than once in MythTV, but I know that you can manually switch the tuners from the command line

sudo apt-get install ivtv-utils 

To see what inputs are available:  v4l2-ctl --list-inputs
To see what input it's currently set to: v4l2-ctl --get-input
To set it to input 1: v4l2-ctl --set-input=1

I used this what I was digitizing our old vcr collection.

HTH

---

### Post by klc5555 on 2009-06-07
> **cleanroom said:**
> Hi,
   I'm running Mythbuntu 8.04 with a PVR-150 card.  I have analog cable input into the tuner input of the card and my VCR connected to the composite input of the card.  I have been unable to discover a way to switch from tuner view to view input on the composite terminals.  
I'm sure this is simple and probably trivial any help?

Cleanroom

Go into the backend setup. In Video Sources, add a new video source. Call it, say, "VCR". No grabber.

In Input Connections, associate the new source "VCR" with the 150's composite input. You can assign it a startup channel of, say, "3" or whatever if you wish, but this is not strictly necessary. You will want to associate "VCR" and tv section of your PVR 150 into the same recording group (not "Generic"), so Myth knows it can't record on the 150 while you're watching a tape on the VCR.

When you go back into your mythfrontend and begin watching livetv, whenever you pull up the onscreen menu with "m", now in the "Switch Inputs" dropdown, "VCR" will appear as one of the "tuners" you can switch to.

---

### Post by cleanroom on 2009-06-08
Thanks, 
   I'm still having trouble. When I exit the backend I get a warning that Card 1 (Composite 1) is set to start on channel Please add, which does not exist.
Do you want to fix this problem?
I only have the first of the two input groups changed to something other than generic.
If I exit with the problem in place and without resolving the issue if I try and watch TV the screen just goes blank and the returns to the main menu.  It never lets me watch TV.  I'm sure I'm close, but not sure how the add the channel that does not exist.

---

### Post by cleanroom on 2009-06-09
OK, The TV not working had to to with a permissions problem in a directory that I changed.  
However, when exiting the backend setup I still get the warning "Card 1 (Composite 1) is set to start on channel Please add, which does not exist.
Do you want to fix this problem?"

I only have the first of the two input groups changed to something other than generic.
When I watch live TV, and press M there is no option to switch to composite 1 or VCR which I have renamed it to.

I'd appreciate any help you can offer.

---

### Post by klc5555 on 2009-06-09
> **cleanroom said:**
> OK, The TV not working had to to with a permissions problem in a directory that I changed.  
However, when exiting the backend setup I still get the warning "Card 1 (Composite 1) is set to start on channel Please add, which does not exist.
Do you want to fix this problem?"

I only have the first of the two input groups changed to something other than generic.
When I watch live TV, and press M there is no option to switch to composite 1 or VCR which I have renamed it to.

I'd appreciate any help you can offer.

I'm not sure I understand this properly. So you have set up a new Video Source for your VCR and configured it with "no grabber". You have gone into "Input Connections" and associated it with the composite input of your PVR 150. You've exited the backend setup, run mythfilldatabase in the usual fashion, restarted the backend and returned to "LiveTV". When you press "m" for the onscreen menu, you either have no entry "Switch Input" (you may have to scroll down a bit for it)?, or, having found "Switch Input", you find no entry for your new Video Source "VCR"?

You named the Video Source "VCR", but when you associated it with your composite input in Input Connections, did you also name it there(in the "optional" name line)? (Same with whatever you call your tv connection in the tv tuner part of the Input Connection setup for your pvr150). It will be this assigned name that appears in the Switch Input dropdown in the "m" onscreen menu in live tv. If you have left the name a blank space, that's what you see in Switch Input in the livetv onscreen menu. 

Make sure the VCR is on and cranking out a signal through the composite cables before you attempt to switch to that input.

Finally, I don't whether this is true, but it may be possible that the mythtv 0.21-with-up-to-the-nanosecond-fixes that ships with Mythbuntu 9.04 is a bit fussier about the "is set to 'add channel' which doesn't exist" error than original-issue 0.21 from a year ago was; if it is, you can assign "VCR" a dummy channel in the backend setup to start up on: 2, 3, 98, whatever, and then edit that channel (under the VCR input connection only, not your tv tuner's input connection) in Channel Editor to not appear in the program guide. In all cases, you still switch back and forth between livetv and "VCR" by using Switch Inputs in the onscreen "m" menu. 

The keyboard shortcut "y" should also switch back and forth among your various pvr150 inputs even without using the onscreen menu.

---

### Post by cleanroom on 2009-06-09
OK,
   I still get the channel not assigned error in the backend, but it works!  Thanks!  I cannot find the switch to "VCR" in the menu, but pressing "Y" on the keyboard toggles between Tuner 1 and VCR. Thanks for you help.

---

