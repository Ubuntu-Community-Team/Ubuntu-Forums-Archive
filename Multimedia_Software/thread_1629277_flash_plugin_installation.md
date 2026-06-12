---
title: "flash plugin installation"
date: 2010-11-23
forum: Multimedia Software
---

### Post by srdjan.stanojevic on 2010-11-23
can somebody please help me with flash plugin installation... i tried many ways nothing works. untill today everything worked fine, than i made something wrong. i cant remember what. i have ubuntu 10.04 and i use mozilla 3.6. problem is with videos on youtube and vimeo they dont want to start....thanx.......

---

### Post by lovinglinux on 2010-11-23
Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

---

### Post by srdjan.stanojevic on 2010-11-23
wow, great add-on. thanx a lot man!

---

### Post by lovinglinux on 2010-11-23
> **srdjan.stanojevic said:**
> wow, great add-on. thanx a lot man!

You are welcome.

---

### Post by srdjan.stanojevic on 2010-11-24
i have another problem, mozilla doesnt work at all. it worked few hours after i installed this add-on, than i dont know what happened. when i open it it just stucks and i have to do force quit. any help??

---

### Post by lovinglinux on 2010-11-24
Start in safe mode and disable the add-ons

See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by srdjan.stanojevic on 2010-11-24
i think is ok  for now, except is not firefox anymore, but namoroka. everything works, if i have more problems i'll say...thanx

---

### Post by lovinglinux on 2010-11-24
> **srdjan.stanojevic said:**
> i think is ok  for now, except is not firefox anymore, but namoroka. everything works, if i have more problems i'll say...thanx

Is Namaroka because you are using a ppa for Firefox, probably ubuntu-mozilla-daily, and thus you are getting development versions of it.

To go back to the original Firefox, disable that ppa in Software Center and then re-install Firefox.

```
sudo apt-get install --reinstall firefox
```

I presume you can safely re-enable FLASH-AID, since the problem is most likely to be related to your firefox version. I never received any report of my add-on causing issues like that.

---

### Post by srdjan.stanojevic on 2010-11-24
i came on this option on another forum. but now i think all is ok. if i have problems i do this........

---

