---
title: "ATI DRI Working, Now system hangs?"
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by open_coder on 2006-09-18
Alright. I have a fresh install of 6.06. I installed the fglrx driver and got dri working. But now the system just hangs. I switched back to the old ati driver. I think the problem might be that my card isnt opengl 2.0 compliant. Does anybody else have this problem or know how to solve it.

I have an ATI Radeon 9600 using the latest driver.

All help appreciated.

---

### Post by open_coder on 2006-09-19
Well.. I think it might be a bug in the driver. But when I tried to install the old driver, it didnt enable direct rendering. So I guess I am stuck.

---

### Post by FyreBrand on 2006-09-19
Have you tried fitzman49's [**HowTo: Fglrx 8.26.18 Driver Installation**]("http://www.ubuntuforums.org/showthread.php?t=204910")?  It is very thorough.

---

### Post by open_coder on 2006-09-20
Yeah I couldn't get the dri working with that walkthrough though. When I just installed the package from the ubuntu repos and configured it, it worked. I had to disable compositing, but it worked. The problem I seem to be having has occured to other people with older cards than mine, specifically the 9200. But, nobody every found a fix. 

I think that its just a problem with the driver. When dri is disabled, the card runs fine. I tried to disable the OpenGlOverlay option, but that didnt help. I managed to get rid of the r300 ctx pointer error with the default driver though. I really want to get the fglrx module running so I can start playing games and I want to use XGL. I have been dual booting for a long time in order to play games simply because I don't have an nvidia card and can't get my ati card to work properly. Recently, I just got rid of windows and want to use only linux.

Thanks.

---

