---
title: "help required with sound"
date: 2011-03-26
forum: Multimedia Software
---

### Post by wifyonk on 2011-03-26
ok this is where im at ,i have a soundblaster audigy 2 zs and a gtx 460 graphics card ,the problem im having is getting any sound ,hdmi or through the audigy,i have manualy set the audigy in alsamixer as the default sound card,i have disabled the nvidia sound and still get nothing,although if i boot ubuntu in safe mode without the graphics driver the sound works fine ,so im assuming its the nvidia graphics driver thats causing the problem,any help would be appreciated

---

### Post by wifyonk on 2011-03-27
anyone i know its the nvidia driver causing it i just need a solution ,

---

### Post by wifyonk on 2011-04-01
bump ,anyone ?

---

### Post by Yellow Pasque on 2011-04-01
Blacklist the snd-hda-intel driver
```
echo "blacklist snd-hda-intel" | sudo tee /etc/modprobe.d/blacklist.conf
```

---

### Post by wifyonk on 2011-04-03
this worked perfect,blacklisted then restarted ,ran alsamixer and unchecked the digital output and now the sound works fine thankyou for the help,i know many people with the gtx sound cards seem to be getting this problem ,thanks for the fix

---

