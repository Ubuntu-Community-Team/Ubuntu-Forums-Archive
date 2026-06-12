---
title: "Problem with new video card, please help"
date: 2009-07-16
forum: Multimedia Software
---

### Post by nix-n00b on 2009-07-16
Hello everybody,

     I am running Ubuntu Juanty and currently am useing my built in nvidea video card which is built into the motherboard. I recently purchased a new video card a 1GB Radeon HD 4650 and installed it, i can see the fan on the video card turning so it seems to be working, except whenever i plug my monitor into it the screen is completely black. I can not even see the bios screen when you first turn the pc on to press del to goto setup. 

    The installation cd that came with the card seems to be no good because it is for windows (the install cd with the drivers) any ideas on how to fix this? any help would be greatly appriciated. Thanks!

---

### Post by lukeiamyourfather on 2009-07-16
Most likely you'll need to disable the onboard video card or at least set the BIOS so the added video card is the primary display adapter. Without setting that in the BIOS it assumes you want to use the onboard video at the BIOS level and might even ignore any other graphics cards.

Once that's taken care of you should be able to add the drivers through Ubuntu itself. Use the hardware drivers in the administration menu and it should show any available proprietary drivers for the card. Enable them and it should install and restart the system. Cheers!

---

### Post by wojox on 2009-07-16
The only thing I could think would be to take the new card out so it boots with old card and go into BIOS and see if you can disable the on board video.

---

### Post by nix-n00b on 2009-07-16
Thanks, I tried to look in BIOS for a setting to disable the onboard video card and did nto see one, so im downloading the motherboard manual right now to try and figure out how to disable it from the mother board, there maybe some kind of jumper or something i need to disconnect to disable the onboard one. I've always did it on other computers easy threw bios, my mother board is this one [http://www.gigabyte.com.tw/Support/Motherboard/Manual_Model.aspx?ProductID=2507](http://www.gigabyte.com.tw/Support/Motherboard/Manual_Model.aspx?ProductID=2507) (model: gigabyte [COLOR=Black][COLOR=#FD6724]GA-M61SME-S2)


[/COLOR][/COLOR]

---

### Post by nix-n00b on 2009-07-16
Ok, I researched the manual of the motherboard and found I can do it threw an advanced BIOS setting by selecting it to boot from the PCE? (PCI-Express) slot before it uses the onboard one, no option to completely disable the onboard one. So i selected it to boot and use the new card useing PCI express slot first which the new video card is in..

It booted to a blank/black screen again, so i switched the vga cord back into the onboard vga, and it booted blank/black screen this time, so I had to take the CMOS battery out and put it back into the mother board to reset the BIOS settings and took the new card out and now it works again..

is it possible that my motherboard does not support the video card? it says in the specs it should, this is the exact card i have

```

http://cgi.ebay.com/ATI-Radeon-HD-4650-1GB-DDR2-PCIE-HD4650-HDMI-Video-Card_W0QQitemZ370165499254QQcategoryZ3762QQcmdZViewItemQQ_trksidZp2773.m263QQ_trkparmsZalgo%3DSIC%26its%3DI%252BC%26itu%3DUCI%252BIA%252BUA%252BFICS%252BUFI%26otn%3D38%26po%3DLVI%26ps%3D54
```

and this is my motherboard

```

http://www.gigabyte.us/Products/Motherboard/Products_Overview.aspx?ProductID=2507
```

I just got a new HD tv and am anxious to hook my computer up to it using the new card, any help is apprieciated, thank you~! :D

---

### Post by lukeiamyourfather on 2009-07-16
Its possible that the motherboard might need a BIOS update. Hard to say with what you've posted though. Does the card have a power cord that needs to be plugged in? Does the card work in another computer?

---

### Post by nix-n00b on 2009-07-16
I dont have another computer to try it on that supports pci express, i looked at the card and theres a wire from the fan that goes to the card (2 prongs), but dont see any other place for a cord to plug in on the card from a PSU

heres what the card looks like

[IMG]http://www.videoinputcc.com/images/Force3D-4650-1GB.jpg[/IMG]

this is my motherboard

[IMG]http://www.gigabyte.com.tw/FileList/Image/motherboard_productimage_ga-m61sme-s2_2.0_big.jpg[/IMG]
I hope its not a faulty card

:confused:

---

