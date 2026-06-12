---
title: "MythTV and XBMC / XBMC-PVR 'integration' via Workspaces"
date: 2012-02-08
forum: Multimedia Software
---

### Post by guyrichie@hotmail.com on 2012-02-08
**Preface**
The reader should acknowledge that other media centre and PVR software does exist.  The methods described below can be adapted to suit your personal preference of software.

NB: The writer assumes the reader is familiar with both MythTV, XBMC, LIRC and LIRCX in terms of setup and day-to-day usage.  A basic knowledge of scripting and the use of the bash terminal is also required.

**Abstract**
A working method of 'integrating' MythTV and XBMC / XBMC-PVR.  This method allows the user to switch between MythTV, XBMC and if desirable test XBMC-PVR and gradually phase out MythTV if XBMC-PVR becomes more suitable to the user.  The transition between MythTV and XBMC is illustrated herein via the use of Workspaces.  By using Workspaces the user can instantly switch between the aforementioned software, without the need of killing processes or waiting for programs to start-up, giving a more 'integrated' experience.

**Introduction**
While there are many users of both MythTV and XBMC, it would appear that many favour using the two programs together for a complete HTPC experience.  This narrative will suggest the key limitations of both MythTV and XBMC that drives this trend.  It will then discuss how through the use of Workspaces and intermediate remote control (lirc) configuration how these two programs can appear more 'integrated'.  Lastly, with XBMC-PVR becoming more stable this narrative will give an example how the described 'integrated' technique can be gradually phased out to give rise to sole use of XBMC-PVR - if desired.

**MythTV & XBMC**
MythTV is perfectly capable of performing the tasks to which XBMC can.  For instance, by installing the plug-ins and add-on components, such as MythWeather, MythGallery, MythVideo and  MythMusic, MythTV will be able to perform the default playback tasks of XBMC.  However, many favour XBMC over these plug-ins and add-ons for its aesthetic appearance and ease of use.  This results in users demanding XBMC to have a PVR function to match that of MythTV ( - or MythTV to have a skin and ease of use to match that of XBMC – this discussion is beyond the scope of this document). 

**XBMC-PVR**
At the time of writing XBMC-PVR (using cmyth) is still under development, yet through the latest testing it appears in a stable enough condition for general day-to-day use.  However, for more advanced use it still lacks the features of MythTV, such as pause and rewind live TV, management of recording conflicts, series record, re-record features etc.

**'Integration' of MythTV and XBMC / XBMC-PVR**
It is common practice to have a button on a remote control that launches a script to switch between MythTV and XBMC.  It is also common to add a menu item in each program to switch between MythTV and XBMC.  Both these methods depend upon either killing a process and/or starting a process.  This involves time; time for a process to be killed, but moreover time for the new process to load.  This narrative suggests that both MythTV and XBMC can be open simultaneously, but open on different Workspaces.  This enables the user via their remote control to instantly switch between MythTV and XBMC / XBMC-PVR.

*Example 1.*
If a user is watching LiveTV in MythTV and wants to listen to Music in XBMC, the user can press the Music button on their remote control; this then instantly stops MythTV playback on Workspace 1, switches to Workspace 2, where XBMC is waiting, and tells XBMC to make the Music library active.

*Example 2.*
If a user is watching a video in XBMC and wants to watch LiveTV in MythTV, the user can press the LiveTV button on their remote control; this then instantly returns XBMC to the home menu, stops playback, switches to Workspace 1, where MythTV is waiting, and tells MythTV to jump to LiveTV 
 - OR -
If a user is watching a video in XBMC and wants to watch LiveTV in XBMC-PVR, the user can press the star (*) button followed by the LiveTV button  on their remote control; this then activates the XBMC-PVR Live TV channel listing window.

These examples and all other jumps between MythTV and XBMC / XBMC-PVR is done just as quick as pressing the button on the remote control!  This speed gives rise to a more 'integrated' feel.  Obviously the choice of skin enabled in both applications will deliver a greater visual 'integration' too.

**How To**
Download the attachment (MythTV&XBMC-pseudo-integration.tar.gz), extract and view README.

Many thanks,
Guy.

---

