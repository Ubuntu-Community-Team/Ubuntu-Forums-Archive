---
title: "No Sound"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by jcouillard on 2007-12-01
I can hear the test sound for login and logout BUT I cannot get any other sound. (i.e. media players, and in Firefox 2.0.0.10, etc.) Does anyone have a basic fix to refresh the systems sound driver or something. I did recently do a fix to get sound on Youtube, but after that I was only able to hear things on Youtube and no sound anywhere else, other than the test sound. This is strange

---

### Post by kyphi on 2007-12-01
The cause of sound problems can be diverse.  Please look at the URL below to see if you can see a solution there:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

Please advise if the solutions described do not solve your problem.

---

### Post by jcouillard on 2007-12-02
> **kyphi said:**
> The cause of sound problems can be diverse.  Please look at the URL below to see if you can see a solution there:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

Please advise if the solutions described do not solve your problem.

For some crazy reason now the sound works, even on youtube, despite me taking away the software that was loaded to help allow for youtube to work. Very strange, I won't touch anything now since it's working. Is Linux known for dropping things like sound constantly, or needing to be rebooted for any reason?

---

### Post by kyphi on 2007-12-02
> ... now the sound works, even on youtube, despite me taking away the software that was loaded to help allow for youtube to work..... Is Linux known for dropping things like sound constantly, or needing to be rebooted for any reason?
Some programmes, not supported by Ubuntu will cause conflicts with installed files.  Skype for example is notorious for doing this.  Perhaps when you removed the un-needed YouTube installation files the conflict was resolved.

When I first started using Ubuntu I broke my system a few times because I ran riot in that Aladdin's Cave called 'The Repositories' where all the software treasures in the world are yours for the taking.  It takes a while to become more discerning and choose programmes more judiciously.

Now my chosen operating system is as solid as a rock.  Good luck with yours.

---

### Post by jcouillard on 2007-12-02
Thanks it will take a while...lol I'm still trying to figure out how to delete the limewire program that seems to not have installed right. It does not even show up in my add/remove programs area. i went into the usr folder to delete it out and it said I did not have the rights

---

### Post by deadgobby on 2007-12-02
At first it sound like you did not disable the on board device in BIOS. If you have a sound card like  sound blaster for example. You'll get the front end sound like the splash log in sound and none in apps like the web. Disabling the on board sound device will have all sounds devert to the sound card.
Gobby

---

### Post by kyphi on 2007-12-02
deadgobby - I second your advice.

jcouillard - whatever you have installed on your system will show up in Synaptic.

Go into Synaptic (System -> Administration -> Synaptic Package Manager and scroll to the entry for limewire.  Right click it and select 'Mark for complete Removal'.  Then at the top of the screen click on Apply.  This will remove limewire and its configuration file.

---

### Post by jcouillard on 2007-12-03
> **kyphi said:**
> deadgobby - I second your advice.

jcouillard - whatever you have installed on your system will show up in Synaptic.

Go into Synaptic (System -> Administration -> Synaptic Package Manager and scroll to the entry for limewire.  Right click it and select 'Mark for complete Removal'.  Then at the top of the screen click on Apply.  This will remove limewire and its configuration file.

Thanks guys, I performed the limewire removal, thanks. I'll look into the onboard sound. Thanks!

---

