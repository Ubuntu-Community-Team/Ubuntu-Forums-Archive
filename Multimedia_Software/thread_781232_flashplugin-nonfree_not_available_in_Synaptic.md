---
title: "flashplugin-nonfree not available in Synaptic?"
date: 2008-05-04
forum: Multimedia Software
---

### Post by 1inxs on 2008-05-04
Unable to play youtube or anything else on wifes PC. I search for flashplugin-nonfree in Synaptic Package Manager and it is NOT available in the list of packages. I've tried 4 or 5 different posts and am unable to get her system working. Where do I start?

---

### Post by NightwishFan on 2008-05-04
Run through these steps and we will likely get it working. In terminal:
```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```
If no go, then do this:
System -> Administrator -> Software Sources
Then check the Universe, restricted and multiverse boxes (pretty much all the boxes ;]), close it and then again open a terminal and run:
```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

---

### Post by 1inxs on 2008-05-04
> **NightwishFan said:**
> 
If no go, then do this:
System -> Administrator -> Software Sources
Then check the Universe, restricted and multiverse boxes (pretty much all the boxes ;])
I think that was it. Thank you!! I'm trying to wean the wife off of MS XP. She has her youtube and that makes her happy. I don't remember this problem when I did my Ubuntu system.

---

### Post by NightwishFan on 2008-05-04
I never had the problem either. I am glad you got it working.

---

