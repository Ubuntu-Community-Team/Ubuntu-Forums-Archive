---
title: "Jack/ Rosegarden/VST/Linux audio Setup"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by mistermax on 2007-03-08
I've just got into the idea of music mashups and want to have a go at this using my Eft system. I've got audacity, rosegarden, and a load of Jack aware software installed. Can anyone point me at a reasonably simple to follow guide on using Jack? The current documentation on the Jack site isn't great...

If anyone has any experience of using rosegarden with VSTcould they give me some tips please?

Has anyone on these forums tried making mashups/remixes etc. with an Ubuntu system..?

---

### Post by eric71 on 2007-03-08
Regarding Rosegarden and vst, it is really quite easy.  You will need to install wine, via synaptic or Adept. You will need to install dssi-vst, for instance the package in this thread(not available from normal Ubuntu repositories) : 

 [http://www.ubuntuforums.org/showpost.php?p=1310545&postcount=13](http://www.ubuntuforums.org/showpost.php?p=1310545&postcount=13)

Create a folder called vst in your home directory and put the dll files of some of your facvorite vst and vsti plugins in it.  When you star Rosegarden, you should have your VST effects available along with the LADSPA effects, and VSTi's available with your DSSI plugins.

---

