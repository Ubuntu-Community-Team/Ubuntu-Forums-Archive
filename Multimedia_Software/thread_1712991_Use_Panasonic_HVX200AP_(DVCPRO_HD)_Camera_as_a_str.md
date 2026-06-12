---
title: "Use Panasonic HVX200AP (DVCPRO HD) Camera as a streaming webcam"
date: 2011-03-23
forum: Multimedia Software
---

### Post by IceDoE on 2011-03-23
Hi, I'm trying to use a Panasonic DVCPro HD camera as a webcam to stream live video from the camera to services like ustream.tv. Currently, the only way I can find to connect the camera to my computer puts the camera into a special pc connect mode (which does not allow recording) and makes the cameras p2 cards detected as drives. Obviously, this doesn't help me do live streaming (I don't even need to record on the camera).

I've seen that on Mac OS X a program called camtwist can be used to do what I want, but it would be nice to find an ubuntu/linux solution. 

Any ideas?

---

### Post by no2498 on 2011-03-23
did you read  the how to for the cam



Camera Fact Sheet – Panasonic DVCPRO HD
Sample workflow
Edit DVCPRO HD from P2 Media
Edit on Media Composer at 1080i/59.94
Output back to DVCPRO HD deck via 1394
Assume HD footage shot in 1080i/60i mode for the following example:
1. Make sure the Panasonic P2 drivers are installed on the editing system.
2. Connect the camera via a USB cable to the PC (note: if using a Mac, then Firewire is the preferred
  connection)
3. The camera’s media switch must be set to P2, which will cause the P2 card(s) to mount as a drive(s). See
    camera User Manual for more details.
4. Start the Avid application. Create a 1080i 59.94 project
(if necessary, select File> Mount all and/or File>Load Media Database to recognize the P2
card(s)added since starting the application.
5.
To play media directly from the P2 card(s), select “File > Import P2 > Clips to Bin”
a.
This will import clips directly to your bin although media will stay on the cards/drives.
b. Double-click the clip and play in a pop-up window or in the source monitor.
c.
6.
The clips are now playable/editable directly from the P2 device
To copy P2 files to a local or networked media drive:
a.
Select the clips you wish to import media for in the bin.
b. Select File > Import P2 > Media.
c.
7.
The application imports the media to your system.
Edit the DVCPRO HD footage
a.
You can mix footage of the same frame rate with SD and/or Avid DNxHD®-based footage of the
same frame rate and frame structure (progressive or interlaced) in real time on the Avid timeline.
b. Variable Frame Rate (VFR) workflow example:
i. Footage recorded at 720p 60 on the camera and played back in the 720p 23.976 Avid
project will result in a smooth 2.5x slow motion effect. Please refer to camera’s User
Manual for directions on shooting in VFR mode.
8.
Output Options
a.
“Writeback” to P2 card media directly with a compatible P2 device.
i. Select Output Menu > Export to Device > P2...”
ii. Set the export settings as desired
iii. Click save

---

### Post by IceDoE on 2011-03-24
What are are describing is how to view, edit, etc. footage and clips already on the P2 card.

What I am asking is how to do live streaming from the camera, and accessing previously recorded data on the p2 cards will not help with this. 

I figured out one step of the process, and that is to set the camera record settings to something other than 720/24p (and some other 720 settings) which for some reason block the stream from going through the firewire. This allows a mac (at least with twistcam, possibly without) to see the Panasonic as a webcam video device and use it. However, so far I have no such luck on my linux machine.

---

### Post by no2498 on 2011-03-25
have you tried it in vlc media player

---

