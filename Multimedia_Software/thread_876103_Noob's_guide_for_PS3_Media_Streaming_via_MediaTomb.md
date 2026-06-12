---
title: "Noob's guide for PS3 Media Streaming via MediaTomb on Ubuntu 8.04"
date: 2008-07-31
forum: Multimedia Software
---

### Post by bemis23 on 2008-07-31
This topic has been rehashed many many times, but I ran into a few confusing issues when I was setting up my media server:

1) Out of the box my PS3 recognized MediaTomb - although when searching for the media server the PS3 says it fails - but MT always shows up as available afterwards.

2) Photos worked flawlessly for me out of the box.

3) Audio and Video (MP3, DivX)

In previous guides where folks have installed MediaTomb seperately from the Ubuntu installation there are 2 config.xml files.  In 8.04 I could only locate one file:

/etc/mediatomb/config.xml

Although editting this one only worked for me.
To actually enable MP3 and DivX streaming edit the config.xml file from the terminal:
[I]
sudo gedit /etc/mediatomb/config.xml[/I]

Scroll down and find the following block of code:

[I]</storage>
    <protocolInfo extend="no"/><!-- For PS3 support change to "yes" -->
    <!--
       Uncomment the lines below to get rid of jerky avi playback on the
       DSM320 or to enable subtitles support on the DSM units
    -->[/I]

Change the option to yes so that the code reads:

[I]</storage>
    <protocolInfo extend="yes"/><!-- For PS3 support change to "yes" -->
    <!--
       Uncomment the lines below to get rid of jerky avi playback on the
       DSM320 or to enable subtitles support on the DSM units
    -->[/I]

You need to make a 2nd code revision here:

[I] <!-- Uncomment the line below for PS3 divx support -->
 <!-- <map from="avi" to="video/divx"/> -->[/I]

Remove the comment tags:

 [I]<!-- Uncomment the line below for PS3 divx support -->
        <map from="avi" to="video/divx"/>[/I]

Save and exit the config file.  At this point go ahead and detach and audio/video media from the MT Database via the GUI (Crossed chains symbol).  

Restart both the server and the PS3 (in that order), and reattach your media.  All files should show up as playable now in from the PS3.  

Voila!

---

### Post by Descendant X on 2008-08-12
While it took me about five or six tries to get this to work, I can finally see the media on my PS3!

On thing I'd like to add here is that I believe that it's best if you do all the setup and file configuration prior to turning on the PS3. I think one of the reasons why I had so much trouble is that I had been turning on the PS3 prior to modifying the config.xml and adding the files. If I did those first and THEN started the PS3 it seems to have worked.

EDIT: I suppose that I should add that you've helped me solve the only problem that would have made revert back to Vista, given the ease of use in sharing media with WMP11. Now that I have Mediatomb up, I have no more reasons.

Thanks!

---

### Post by Aerospaztic on 2008-10-22
Can someone please tell me why gedit won't let me save the code modifications I make?

---

### Post by amak79 on 2008-10-30
> **Aerospaztic said:**
> Can someone please tell me why gedit won't let me save the code modifications I make?

This is because your user doesn't have the necessary permissions to write to the file. When editing files that your user doesn't own, you need to start **Terminal** and use **gksudo gedit /path/to/file** or **sudo nano /path/to/file** instead.

---

### Post by burntresistor on 2009-10-27
I'm having trouble with ubuntu when i try to add the media I have (its all on a external)  I'm getting an error saying I still don't have permission . I edited the files exactly.

---

