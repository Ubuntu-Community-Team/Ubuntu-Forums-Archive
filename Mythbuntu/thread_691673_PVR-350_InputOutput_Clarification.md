---
title: "PVR-350 Input/Output Clarification"
date: 2008-02-08
forum: Mythbuntu
---

### Post by krazyj on 2008-02-08
Alright so let me get this straight...

Is the PVR-350 card capable of handling input AND output simultaneously? For example, if I have only ONE PVR-350 card in my buntu box, is that the only thing I need to hook it up to a TV and use the box as a PVR?

Also, I noticed the SVideo port on here is labelled 'SVideo IN' on the faceplate. Does this mean that I cannot use the SVideo port as a video out?

Thanks!

---

### Post by volkswagner on 2008-02-08
The PVR 350 has svid in and svid out.  The output requires a breakout cable which also carries audio out.

The card sure does input/output at the same time you can watch live tv via the coax in and svid out to your tv, or use the output connection on your vcr, cable box etc. to the svid input.

I dont think the output will display your desktop so administering the box will need to be done with ssh or other remote means.

There is a check box to select "use pvr output" in frontend setup.

---

### Post by andrewb78 on 2008-02-10
Actually, the PVR-350 can display the desktop, but you can run into overscan issues.  See the [PVR-350 HOWTO for Gusty]("https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out").

---

### Post by Chuckels550 on 2008-02-11
The PVR-350 is different form the the other Hauppauge PVRs because it has a physically separated the decoder and encoder, which means that you can watch a recording while recording a program, but the card cannot handle more than one recording at a time.  Compare your PVR-350 to a picture of the PVR-500, which has two decoder/encoders.  The PVR-500 allows you to watch a live TV or a recording while recording something else.  The card also allows you to connect to Cable FM Radio.

Your SVideo In port is useful for editing, but you cannot use it for SVideo Out.  The backpanel or A/V cable has the SVideo Out as well as the Composite video and stereo outputs.  

If you have an Analog TV, then the PVR-350 TV Out is worth setting up, assuming you are not running games that need OpenGL.  If you are connecting to a TV that displays digital quality like an LCD TV, then use a graphics card for the TV Out like a Nvidia Geforce 5200 or better.  The PVR-350 is limited to the resolutions associated with analog tv.  Composite, SVideo, and Component are all analog styles of connection to a TV for display.  Note that the PVR-350 cannot capture Digital TV.

---

