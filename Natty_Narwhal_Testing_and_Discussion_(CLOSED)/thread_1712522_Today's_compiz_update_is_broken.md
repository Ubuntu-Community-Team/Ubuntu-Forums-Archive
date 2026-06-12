---
title: "Today's compiz update is broken"
date: 2011-03-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by encefalocardia on 2011-03-22
Synaptic reported a whole bunch of updates, included compiz. But instead of updating it, it was removed.

I tried to do a manual update and the following error appeared:

```
compiz-plugins-main:
Depends: compiz-core-abiversion-20110224  but it is not installable
```

Uninstalled all the compiz files and purged their settings. Tried to install again and same error. Any ideas?

---

### Post by encefalocardia on 2011-03-22
wtf? I just realized I dont have sound too. That was some update alright!

---

### Post by go7Ul1ai on 2011-03-22
I guess it would have been best that you review the changes before applying? There's a handy sticky post that you may find helpful:
[http://ubuntuforums.org/showthread.php?t=1641400](http://ubuntuforums.org/showthread.php?t=1641400)

---

### Post by encefalocardia on 2011-03-22
I understand Im at fault. Im so used to just click "ok" so I can focus on other tasks while synaptic updates. However I just wanted to know if this can be fixed.

BTW. I resolved the sound issue by changing the "connector" option in the output tab in sound prefs. Dont know why changed.

---

### Post by go7Ul1ai on 2011-03-22
> **encefalocardia said:**
> I understand Im at fault. Im so used to just click "ok" so I can focus on other tasks while synaptic updates. However I just wanted to know if this can be fixed.

BTW. I resolved the sound issue by changing the "connector" option in the output tab in sound prefs. Dont know why changed.

Are you able to force version (in synaptic) to the previous packages?

---

### Post by encefalocardia on 2011-03-22
Seems that whatever was broken it's resolved now. Reloaded the reps and tried again and this time installed correctly. Sorry for taking your time.

---

### Post by go7Ul1ai on 2011-03-22
> **encefalocardia said:**
> Seems that whatever was broken it's resolved now. Reloaded the reps and tried again and this time installed correctly. Sorry for taking your time.

No don't apologise, that's good news. Glad it's all fixed for you :)

---

### Post by gunbladeiv on 2011-03-23
can you tell me a lil bit more specific on what fix your compiz? cause i dealing with the same crash on compiz. some plugin missing and no window decorator nor unity panel visible or can be run on boot.  Right now im on classic desktop and running metacity.

---

### Post by encefalocardia on 2011-03-23
Honestly I cant. It happened just as I said. Fired up Synaptic, reloaded the reps and it fixed by itself. Have you tried to follow the steps I did?

```

sudo apt-get remove compiz*
sudo apt-get autoremove
sudo apt-get update

```

Launch Synaptic and select Compiz again. Check that the plugins list includes compiz-plugins-main. Update.

---

### Post by Harry33 on 2011-03-23
There is nothing to fix, there is no bug in this respect.
It is just that people try to upgrade a set of packages (this time Compiz) before all of its component packages are uploaded into Natty repositories. This is a very common reason to failures.

Concerning the virtual package "compiz-core-abiversion", please read the following.

1. The packages compiz-core 1:0.9.4git20110322-0ubuntu
     provides the virtual packages compiz-core-abiversion-20110322.

2. The package compiz-plugins-main 0.9.4git20110322-0ubuntu1
    depends on the very same virtual package compiz-core-abiversion-20110322

So they match perfectly. But if only the older version of compiz-core was still in repos, the dependency was not yet met.

---

### Post by encefalocardia on 2011-03-23
> **Harry33 said:**
> There is nothing to fix, there is no bug in this respect.
It is just that people try to upgrade a set of packages (this time Compiz) before all of its component packages are uploaded into Natty repositories. This is a very common reason to failures.

Concerning the virtual package "compiz-core-abiversion", please read the following.

1. The packages compiz-core 1:0.9.4git20110322-0ubuntu
     provides the virtual packages compiz-core-abiversion-20110322.

2. The package compiz-plugins-main 0.9.4git20110322-0ubuntu1
    depends on the very same virtual package compiz-core-abiversion-20110322

So they match perfectly. But if only the older version of compiz-core was still in repos, the dependency was not yet met.

Yeah, but the update was released hours ago. It's not normal that he's still experiencing this problem, right?

---

### Post by Harry33 on 2011-03-23
> **encefalocardia said:**
> Yeah, but the update was released hours ago. It's not normal that he's still experiencing this problem, right?

It is normal.
The fact that a certain update is released does not guarantee it is uploaded into all Natty source servers throughout the world at the same time. It may take a whole day until it reaches all servers.
We do not know what source server he is using with software-sources application.

---

### Post by jocko on 2011-03-23
> **encefalocardia said:**
> Yeah, but the update was released hours ago. It's not normal that he's still experiencing this problem, right?
Perfectly normal if he use repos from a local mirror instead of the main server. It takes time to sync all the mirrors...

---

### Post by encefalocardia on 2011-03-23
You're right, forgot that. That's why Im cheating. I live in mexico but use USA servers, they get the updates first.

---

### Post by gunbladeiv on 2011-03-23
and im using main server as my software source. but maybe it happen because incomplete update in repository. NVM, i'll wait till there is another update on Natty. And we will look at how things go from there.

---

### Post by kuvanito on 2011-03-23
after yesterday's update i had an error telling me that ubuntu desktop could not be installed,after a reboot i lost my desktop,plain wallpaper,done everything i could to bring unity back on,no way,someting to do with compiz,got to go,will try later;)

---

