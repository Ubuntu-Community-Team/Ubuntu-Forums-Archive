---
title: "MythTv plugins not working after update"
date: 2010-01-17
forum: Mythbuntu
---

### Post by nasevz on 2010-01-17
I am using Avenard's repository for MythTv and upgraded to latest trunk version for karmic.
After upgrade, all plugins have problem initializing (binary version does not match libraries) and are not working.
Is there anything I can do, or should I wait for another update with correct plugin version?

```
2010-01-17 11:15:30.019 Plugin mytharchive (0.23.20100101-1) binary version does not match libraries (0.23.20100115-1)
2010-01-17 11:15:30.019 Test Popup Version Failed 
2010-01-17 11:15:30.019 Unable to initialize plugin 'mytharchive'.
2010-01-17 11:15:30.021 Plugin mythbrowser (0.23.20100101-1) binary version does not match libraries (0.23.20100115-1)
2010-01-17 11:15:30.021 Unable to initialize plugin 'mythbrowser'.
2010-01-17 11:15:30.052 Plugin mythflix (0.23.20091112-1) binary version does not match libraries (0.23.20100115-1)
2010-01-17 11:15:30.052 Unable to initialize plugin 'mythflix'.
2010-01-17 11:15:30.060 Plugin mythgallery (0.23.20100101-1) binary version does not match libraries (0.23.20100115-1)
2010-01-17 11:15:30.060 Unable to initialize plugin 'mythgallery'.
2010-01-17 11:15:30.062 Plugin mythgame (0.23.20100101-1) binary version does not match libraries (0.23.20100115-1)
2010-01-17 11:15:30.063 libmythgame.so/main.o: binary version mismatch
2010-01-17 11:15:30.063 Unable to initialize plugin 'mythgame'.
2010-01-17 11:15:30.064 Plugin mythmovies (0.23.20100101-1) binary version does not match libraries (0.23.20100115-1)
2010-01-17 11:15:30.064 libmythmovies.so/main.o: binary version mismatch
2010-01-17 11:15:30.065 Unable to initialize plugin 'mythmovies'.
2010-01-17 11:15:30.168 Plugin mythmusic (0.23.20100101-1) binary version does not match libraries (0.23.20100115-1)
2010-01-17 11:15:30.168 Unable to initialize plugin 'mythmusic'.
2010-01-17 11:15:30.173 Plugin mythnews (0.23.20100101-1) binary version does not match libraries (0.23.20100115-1)
2010-01-17 11:15:30.173 Unable to initialize plugin 'mythnews'.
2010-01-17 11:15:30.180 Plugin mythvideo (0.23.20100101-1) binary version does not match libraries (0.23.20100115-1)
2010-01-17 11:15:30.180 Unable to initialize plugin 'mythvideo'.
2010-01-17 11:15:30.184 Plugin mythweather (0.23.20100101-1) binary version does not match libraries (0.23.20100115-1)
2010-01-17 11:15:30.184 Unable to initialize plugin 'mythweather'.
```

---

### Post by zaurus on 2010-03-02
What is Avenard´s repository?
Personally I was foolish enough to activate dally builds against 0.23 trunk. Well the result as always the same Mythbuntu does not work. I am so tired now with Linux and Mythbuntu in particularly.

Sorry, it is not the answer on your question because I do not have one.

---

### Post by tgm4883 on 2010-03-02
> **zaurus said:**
> What is Avenard´s repository?
Personally I was foolish enough to activate dally builds against 0.23 trunk. Well the result as always the same Mythbuntu does not work. I am so tired now with Linux and Mythbuntu in particularly.

Sorry, it is not the answer on your question because I do not have one.

Helpful.

@OP  I would try doing the update again, looks like the plugins didn't get updated

---

### Post by azmyth on 2010-03-03
When I was using Avenard's repo, I'd run into issues like this. One time it installed but didn't update that a newer backend as it said the package was broken thus it didn't update my plugins since it thought I was on an older version. I think I rebooted and did the update again and it took.

---

### Post by zaurus on 2010-03-03
> **azmyth said:**
> When I was using Avenard's repo, I'd run into issues like this. One time it installed but didn't update that a newer backend as it said the package was broken thus it didn't update my plugins since it thought I was on an older version. I think I rebooted and did the update again and it took.
What plugins shuld I update, all? And how, update-manager tells my system is up to date. Should I reinstall all?

KR

---

### Post by mrand on 2010-03-20
> **zaurus said:**
> What plugins shuld I update, all? And how, update-manager tells my system is up to date. Should I reinstall all?

KRI would try removing mythflix - it does not work with 0.23.

[INDENT]   Marc[/INDENT]

---

