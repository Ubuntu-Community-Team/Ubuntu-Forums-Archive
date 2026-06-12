---
title: "Can you reduce the gui down to just videos?"
date: 2012-10-05
forum: Mythbuntu
---

### Post by RTIInstaller on 2012-10-05
I only want this machine to play back a pre existing movie library, there wont be a tuner card or anything else like that installed. Can i remove any reference to anything other than "videos" from the front end gui?

Thank you     :popcorn:

---

### Post by nickrout on 2012-10-05
If that is what you want I wonder why you are using mythtv at all. It is primarily for recording TV. You might be better with xbmc. 

But you could edit MythTV's menus. They are xml files. Move them into ~/.mythtv/

---

### Post by RTIInstaller on 2012-10-05
I have heard of xbmc but have no experience with that at all?

How would one go about editing the GUI  XML for myth?

:smile:

---

### Post by nickrout on 2012-10-05
At it's simplest create a file ~/.mythtv/mainmenu.xml. put this in it:

<?xml version="1.0" encoding="UTF-8" ?>
<mythmenu name="MAIN">
 

<button>
   <type>VIDEO_BROWSER</type>
   <text>Watch Videos</text>
   <description>Browse your video library</description>
   <action>JUMP Video Default</action>
</button>

</mythmenu>

---

### Post by RTIInstaller on 2012-10-05
> **nickrout said:**
> At it's simplest create a file ~/.mythtv/mainmenu.xml. put this in it:

<?xml version="1.0" encoding="UTF-8" ?>
<mythmenu name="MAIN">
 

<button>
   <type>VIDEO_BROWSER</type>
   <text>Watch Videos</text>
   <description>Browse your video library</description>
   <action>JUMP Video Default</action>
</button>

</mythmenu>
):P
Thanks! and wow XBMC is cool I think that might be the ticket to happy times

---

### Post by nickrout on 2012-10-05
Well mythtv's raison d'etre is as a TV recording setup, and it is also a very competent video library, music library, internet video viewer etc. But if you don't want the TV recording, XBMC is probably easier. Just set up your central server to share all the video files via cifs (that's windows networking) and bob's your uncle.

---

