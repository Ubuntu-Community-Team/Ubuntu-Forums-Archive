---
title: "video card problem ATI Rage 128 Voodoo2"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by helmetator on 2007-05-09
HI, 

i just installed Kubuntu. I had a few problem after the installation cause I was not getting any graphic interface. Just a black screen with a blinking cursor.
Right now I get the graphic interface but when I go to system configuration/monitor and display to adjust my parameters for the display and the graphic board, I get a page with nothing on it (I mean no display icon) and the following message:
"the module Monitor and Display could not be loaded.
 The diagnostics is:
 Possible reasons:
 -An error occured during your last KDE upgrade leaving an orphaned control module
 -You have old third party module lying around.
Check these points carefully and try to remove the module mentioned in the error message.
If this fails, consider contacting your distributor or packager."
Actually, like I said before I have had few problems during installation. Right now 
I still get this "00000000 .....couldn't locate .... ACPI" message. I can get rid of this message by entering the following line in the kernel "noacpi acpi=off apm=on".
PC's configuration is s follow:
-Motherboard:440BX/ZX/DX 82443BX/ZX/DX AGP bridge (rev0.3)
-PentiumIII (Katmai) 451 Mhz
-SDRAM 128Mhz
-Video board:ARI Rage 128 RF/SG AGP with a Multimedi video Controler plugged to it :3DFX interactive Voodoo 2.
-Soundcard: Creative Labs Sb live CT4850.
I installed the following driver for the video card:
-xorg ATI (the one did by ubuntu's team) and the voodoo's driver as well.
I erased all the other one.
Before on windows98SE I didn't have theses problems, so I don't think it's a bad hardware  
configuration. I think it is a video driver problem. Maybe Kubuntu is thinking I have 2 video cards.
Ok, looking forward to hearing from you. I think KDU's graphic interface is great.
Thanks by advance.

---

### Post by jrusso2 on 2007-05-09
I would check to see if xorg ati supports the ATI rage 128 thats a pretty old card.

---

### Post by helmetator on 2007-05-09
Thanks for the answer.
It looks it does.It was written it supports all 128 and Rage type ATI's cards.

---

