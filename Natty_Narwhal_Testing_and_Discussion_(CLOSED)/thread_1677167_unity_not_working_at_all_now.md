---
title: "unity not working at all now"
date: 2011-01-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2011-01-28
Since the last lot of compiz updates when i boot the computer and goto ubuntu desktop session and logon i get desktop with unity launcher etc but cant do anything. when i click icons nothing happens. 

reading the changelogs of the compiz package they have removed the patch to see if system hangs. 

i so pose that mine does... 

does anyone know if there is a bug for this to or should i raise new one.

---

### Post by vmonkey on 2011-01-28
It is a bug, I posted it here: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/709264](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/709264)
Solution is```
 sudo apt-get remove unity-place-files unity-place-applications 
```

So it is not problem of Compiz, but of Unity (try to run Ubuntu Classic desktop, which works even with Compiz)

---

### Post by terry_gardener on 2011-01-28
> **vmonkey said:**
> It is a bug, I posted it here: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/709264](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/709264)
Solution is```
 sudo apt-get remove unity-place-files unity-place-applications 
```

So it is not problem of Compiz, but of Unity (try to run Ubuntu Classic desktop, which works even with Compiz)

thanks works now

---

