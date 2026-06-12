---
title: "digital microscope (gspca, sn9c10[1 2]) - can't correct brightness"
date: 2009-02-12
forum: Multimedia Software
---

### Post by jglepage on 2009-02-12
I have a digital microscope (Konuspix #5023).  Basically it's a cheap optical microscope that comes with an equally cheap webcam that clamps on the eyepiece.   When not attached to the microscope, the webcam functions as a normal webcam.

The webcam in question seems to be well supported under linux.   The system recognizes the camera and loads kernel modules gspca and sn9c102.  

In webcam mode (that is, not attached to the microscope and fitted with a normal lens), the webcam runs extremely well under both camarama and vlc.  However, when I attach it to the microscope and turn on the microscope's built-in light source, the intensity of the light completely overwhelms the camera.  All I see is white.  I have tried to use the brightness/contrast settings on camarama/vlc to adjust for this, but no setting seems to work.

The microscope works OK under windows.   

How can I get linux to automatically adjust for the light intensity?  Or should I just get a filter for the light source?

---

### Post by jglepage on 2009-02-12
Follup:
I determined that the problem is the light intensity.  I did this by the brilliant technique of looking at a piece of fabric; this cut down the light intensity and simultaneously gave me something to look at.  Sure enough, the camera works find under these conditions.  

This camera works fine in low light conditions, but is hopeless in high light.  It works fine with windows, so it's definitely a software problem.  

Does anyone know how to set up mplayer or vlc to capture video in high light conditions?  When I connect the camera, it shows up as a USB camera nd both gspca and sn9c10[1 2] are loaded.  Both vlc and mplayer treat it as v4l.

---

### Post by MaximB on 2009-05-03
Hello

I myself thinking about buying a USB microscope - have you manage to solve your problems ?
What exact model do you have ?
Does it work well in Ubuntu 9.04 64-bit ?

How about viewing water molecules in this kind of microscope ? (for my little experiment).

---

