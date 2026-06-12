---
title: "kubuntu feisty wont detect monitor/vid card"
date: 2007-05-24
forum: Multimedia &amp; Video
---

### Post by twidget on 2007-05-24
Hi
I just installed kubuntu feisty on my new htpc setup. The video card is an Nvidia geforce4
i had to use a different monitor during installation because the feisty installer hangs during installation if you dont have a wired connection to the net. After installing the OS i installed the nvidia driver. When i restarted i got the nvidia splash screen so im pretty sure it originaly worked. I then moved the computer back into my room and connected it to my lcd tv and ran dpkg-reconfigure  xserver-xorg. i noticed 2 things: the video card is detected as "generic video card" , and my lcd tv is detected as "generic monitor" using a different motherboard and kubuntu edgy both of these were properly detected and setup. now the highest resolution i get is 800x600 and i get no nvidia splash on startup. i have a sneaky feeling that dpkg is trying to use the motherboard's onboard video instead of the agp card. I have gone into the bios and set the primary video interface to agp but this didnt seem to help. Is there anything else i can try or should i give up and go back to edgy on this pc?

---

