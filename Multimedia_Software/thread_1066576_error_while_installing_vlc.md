---
title: "error while installing vlc"
date: 2009-02-11
forum: Multimedia Software
---

### Post by earthtux on 2009-02-11
Hi all
I am using 8.10 on a x61t laptop
when I tried to install vlc via synaptic
I got this error
```

E: /var/cache/apt/archives/vlc-data_0.9.4-1ubuntu3_all.deb: unable to move aside `./usr/share/locale/co' to install new version

```

I try to get into the /usr/share/locale to remove co manually
but I got error msg after I issue
```
#/usr/share/locale/>sudo rm co
```
i got this error
```
rm: cannot remove `co': Operation not permitted

```
This is so wierd.........
anyone can help me pls?
thx!

---

### Post by redroad55 on 2009-02-11
If you go to synaptic and locate the pkg. there > right click on it > then click on dependencies you can see the probable reason or reasons why > then use synaptic to uninstall and it will tell you what other pkgs. it would have to uninstall to make that possible..The other possibility might be although the upgrade you are trying to install exists the upgrade for the dependencies is not yet available .. I hope this helps .. Post back any results and or questions .. Best to you

---

### Post by earthtux on 2009-02-11
> **redroad55 said:**
> If you go to synaptic and locate the pkg. there > right click on it > then click on dependencies you can see the probable reason or reasons why > then use synaptic to uninstall and it will tell you what other pkgs. it would have to uninstall to make that possible..The other possibility might be although the upgrade you are trying to install exists the upgrade for the dependencies is not yet available .. I hope this helps .. Post back any results and or questions .. Best to you

hi thx for you reply,
so I went to synaptic and located this vlc-data package
but I didnt find anything telling me y it couldnt reomve that co file
Did i misunderstand what you said?
sorry I am a new ubuntu user........

---

### Post by redroad55 on 2009-02-11
edited version:
> If you go to synaptic and locate the pkg. there > right click on it > in drop dow n choose properties >then click on dependencies you can see the probable reason or reasons why > you can also use synaptic to uninstall and it will tell you what other pkgs. it would have to uninstall to make that possible > here's how when you've located the pkg. click on the green box which indicates it was installed already > a drop down will open , choose "mark for removal" > another window opens and lists if there is other dependencies effected by removal > you can hit cancel and post the Info back and we can go from there..The other possibility might be although the upgrade you are trying to install exists the upgrade for the dependencies is not yet available .. I hope this helps .. Post back any results and or questions .. Best to you
Post back with any results and or questions ..Best to you

---

### Post by earthtux on 2009-02-11
I tried to install the packages separately but still couldnt get around that error I stated above..........
Is there anyway can remove that co file manually? 
or
is there anyway to find out what program is using the co file?

or is there anyway to work around it?
thx

---

### Post by redroad55 on 2009-02-11
In order to understand the conflict I need for you to list what is shown in the steps provided above:
> here's how when you've located the pkg. click on the green box which indicates it was installed already > a drop down will open , choose "mark for removal" > another window opens and lists if there is other dependencies effected by removal > you can hit cancel and post the Info back and we can go from there..

If there is a part of this you are not understanding ..Post back with your question and I will help you..No worries ..Peace out

---

