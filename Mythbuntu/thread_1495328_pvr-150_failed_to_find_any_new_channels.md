---
title: "pvr-150 failed to find any new channels"
date: 2010-05-28
forum: Mythbuntu
---

### Post by zapstrap on 2010-05-28
I have an hvr-1600 and a pvr-150 in the same box.  The box is both front and back end.  If I shutdown the front and backend, run backend-setup, select the pvr-150 tuner and scan for channels, the scanner appears to find all channels, but at the end, it says "Failed to find any new channels!"  If I enter the channel editor, I can see that I only have channels present for the hvr-1600.  I can restart the backend, launch the front end, and use the pvr-150 to tune channels, but if I try to edit the channel table with the web interface, there are no pvr-150 channels present.  I tried deleting both analogue tuners, adding them both back, and scanning both.  Both report the same "Failed to find any new channels" message, but the channels from the hvr-1600 are present.  Is this a permissions problem?  If not, can anybody tell me why it won't add the channels?

---

### Post by klc5555 on 2010-05-28
> **zapstrap said:**
> I have an hvr-1600 and a pvr-150 in the same box.  The box is both front and back end.  If I shutdown the front and backend, run backend-setup, select the pvr-150 tuner and scan for channels, the scanner appears to find all channels, but at the end, it says "Failed to find any new channels!"  If I enter the channel editor, I can see that I only have channels present for the hvr-1600.  I can restart the backend, launch the front end, and use the pvr-150 to tune channels, but if I try to edit the channel table with the web interface, there are no pvr-150 channels present.  I tried deleting both analogue tuners, adding them both back, and scanning both.  Both report the same "Failed to find any new channels" message, but the channels from the hvr-1600 are present.  Is this a permissions problem?  If not, can anybody tell me why it won't add the channels?

Since you are (or probably should be) using only one Video Source both for the Input Connection to the analog-only 150 and for the Input Connection to analog side of the 1600, it should not matter whether these analog stations have been found by the analog scan of the 1600 or the 150. The analog tuning information for bringing up the cards is the same. If you edit channel specs via Channel Editor (or Mythweb), you should be editing channels pertaining to the one single "Analog" Video Source. Only the digital side of the 1600 will require its own separate "Digital" Video Source.

There was some problem with analog scanning in Myth 0.22, though the bug's symptoms don't appear to match yours as you have described them. One of the relevant threads is here: [http://ubuntuforums.org/showthread.php?t=1329767&highlight=analog+scanning+bug](http://ubuntuforums.org/showthread.php?t=1329767&highlight=analog+scanning+bug)

---

### Post by zapstrap on 2010-05-28
Yes, I am using one video source for both analogue tuners.  I am also using a second video source for digital channels.  I don't think the problem is related to the other thread.

What's getting me is that when I had myth 0.22, and looked at the channels using mythweb, I would get a channel source of '1' for the pvr-150, '2' for the hvr-1600, and '3' for the digital side of the hvr-1600.  Now all I'm getting is 2 & 3.

The thing that was nice about the separate source IDs was I could mask out channels on specific tuners.  The pvr-150 tuner has trouble with some channels which the hvr-1600 handles well.  I could mask out the troublesome channels in the pvr-150 source, and if/when a recording was to be made on one of the channels in question, it would always be recorded using the tuner able to properly pull in the channel.

Do I need to create a third video source for this to work now?

---

### Post by ian dobson on 2010-05-28
> **zapstrap said:**
> Yes, I am using one video source for both analogue tuners.  I am also using a second video source for digital channels.  I don't think the problem is related to the other thread.

What's getting me is that when I had myth 0.22, and looked at the channels using mythweb, I would get a channel source of '1' for the pvr-150, '2' for the hvr-1600, and '3' for the digital side of the hvr-1600.  Now all I'm getting is 2 & 3.

The thing that was nice about the separate source IDs was I could mask out channels on specific tuners.  The pvr-150 tuner has trouble with some channels which the hvr-1600 handles well.  I could mask out the troublesome channels in the pvr-150 source, and if/when a recording was to be made on one of the channels in question, it would always be recorded using the tuner able to properly pull in the channel.

Do I need to create a third video source for this to work now?

Yes, create a third video source, link it to your PVR150 and do a channel scan.

Regards
Ian Dobson

---

