---
title: "resolution is finally working...but i do need to know..."
date: 2009-01-04
forum: Multimedia Software
---

### Post by hoboboot on 2009-01-04
everything in my ubuntu has come together over the last week since fresh install, i've got my wireless card working great and i just installed the via driver for my s3 unichrome pro igp card, and then i've fixed my resolution by changing the screen to an lcd panel larger than the screen is and selecting 1280x768 my monitors max proper resolution... when i go into applications: other: screens and graphics, under video card graphics, it is still saying vesa? 

anyway, i havent finished the last step to enable 3d, which supposedly is able to run compiz, i will check this next, my question is, should it still say its using vesa in there? i thought i just installed the via driver, hmm, and in that list of drivers the unichrome didnt work originally, but so my display is working right now under vesa? can someone explain why its vesa when i installed the driver... also another question, the boot screen resolution, how do i fix that, and or do i have to change it from vesa first? 
ah hell im trying the 3d enabling step right now... can anyone tell me how to fix my boot screen resolution, the one with ubuntu in black with an orange slider bar beneath it during initial booting? that is way off the screens actual size still...



edit:
i did the last step which was to edit /usr/bin/compiz so that whitelist line has via in it...like this:

         WHITELIST="nvidia intel ati radeon i810 via"

and ive done that... im not sure if i have this set up right, but i've got my proper resolution max for the desktop working since having installed the via driver, but it seems im still running vesa mode? is this right? can someone who knows tell me whats going on, am i even using the new driver i've installed from via yet? i installed the driver from [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) which was via-unichrome.83.40692

has it been enabled already too? followed the readme that came with it, and.... my display resolution is proper 1280x768, which is what i was aiming for, but does anyone know if i even fixed it with this driver i installed or not? and that step listed to enable 3d effects for my card ( the step came from the readme, in via's drivers setup thing, is that the only step i really do need to take to enable compiz? if so, im guessing it doesnt work, or, should i not be on vesa mode by now? i need help understanding this, i've installed the official via driver from that site and ... i dont know exactly what to do, i'd like to be able to test some open gl, or see compiz run ... can anyone help me figure this out?

---

