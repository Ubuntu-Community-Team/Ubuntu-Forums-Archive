---
title: "Update Manager not working"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by gjbnh on 2010-09-08
I'm having problems with 10.10. Some update in the last few days caused my update-manager to basically stop. It updates list fine, but when I go to install updates, pushing the install button does nothing. I can update via aptitude, but not with the update-manger. How to I repair?? I've done a reinstall of the update-manager  and it didn't help

---

### Post by NightwishFan on 2010-09-08
Try running the update manager from the gnome terminal and post any interesting output from the terminal here:
```
update-manager
```

---

### Post by gjbnh on 2010-09-09
Thanks for the suggestion. However the terminal provides no feedback for me to paste. Any other ideas?

---

### Post by NightwishFan on 2010-09-09
Try "Completely Removing" the package in Synaptic, then install it again. Do this command:
```
sudo apt-get purge update-manager update-manager-core && sudo apt-get install ubuntu-desktop
```

---

### Post by coffeecat on 2010-09-09
I don't know why update manager has stopped working, but you are using a development release and you should use update manager with great caution anyway before final release. Full story here:

[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

And anyway, 10.10 is still in Beta. Expect breakages. There may be a bugfix in the pipeline. Have you checked the Maverick subforum?

---

### Post by Joeb454 on 2010-09-09
*Thread moved to **Maverick Meerkat Testing and Discussion***

---

### Post by NightwishFan on 2010-09-09
Also please note you should never do a partial upgrade unless you know what you are doing.

---

### Post by Yumi on 2010-09-10
My update manager is not working eighter. I use synaptic-package-manager, status - to be updated and that one works.

Michael

---

### Post by gjbnh on 2010-09-11
Thanks for the last tip. I'm glad neither aptitude or synaptic are broken. I will use them until and if the update manager is once again functional.

---

### Post by coffeecat on 2010-09-11
> **gjbnh said:**
> I will use them until and if the update manager is once again functional.

You didn't understand  the link I posted. Update manager is perfectly functional. The problem is potential archive inconsistencies in the repositories of a development version. This ceases to be an issue when the development version goes final.

---

### Post by gjbnh on 2010-09-13
Ah I see what your saying now. But would I be unable to install all updates, or just some of them if that was the case?

---

### Post by coffeecat on 2010-09-13
> **gjbnh said:**
> But would I be unable to install all updates, or just some of them if that was the case?

As that link explains, if update manager offers you a partial upgrade while Maverick is still in development, don't do it. You may break your system. If it lists upgrade packages without mentioning a partial upgrade then you're probably OK to proceed.

Most people in the testing phase, however, do one of these from the terminal:

```
sudo apt-get update
sudo apt-get upgrade
```or

```
sudo aptitude update
sudo aptitude safe-upgrade
```But look at the terminal output before OK'ing the second command. If anything appears iffy, bail out and check this sub-forum. Expect problems while a version is still in pre-release.

---

### Post by gjbnh on 2010-09-18
Thanks for the input guys; however this was not the result of update-manger wanting me to preform a partial update; it was a however something that broke the update manager which occurred in the last couple of weeks. Being a noobie for all intents and purposes I don't know which package or packages did the breaking. 

Running update-manager from terminal with a sudo, I got the following out put:

ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/client.py", line 291, in _on_property_changed
    self.emit("space-changed", value)
TypeError: could not convert type dbus.Double to (null) required for parameter 0

Googleing it did not provide a solution so I would like more input from people thanks.

---

### Post by cariboo on 2010-09-18
Try running update-manager in a terminal with out using sudo, as the program will ask for authentication when it needs it.

---

### Post by gjbnh on 2010-09-18
I can run update manager from terminal, and it will install any updates it finds; My problem is running from the desktop, it finds updates, but will not install them. Chosing the install button produces a brief hang, and then nothing; updates are not install, and no error messages  appear.

---

### Post by mc4man on 2010-09-18
You could file a bug - would be better if it produced an apport.

maybe try cleaning your cache (sudo apt-get clean
and then re-installing aptdaemon, search it in synaptic and re-install all 4 listed packages.
At this point update-manager uses aptdaemon as the backend (if you were to remove aptdaemon it won't auto switch back to synaptic

---

### Post by gjbnh on 2010-09-21
Thanks for the input guys. It appears that the problem is not restricted to update-manager. Computer janitor also does not work from the desktop; it insists that synaptic or upgrade manager is open, so it can not do its thing. Running both programs from a terminal, and as "sudo" both function as expected. For some reason calls from the desktop for authentication aren't being processed, hence both programs fail from the desktop.

---

### Post by Yumi on 2010-09-21
> re-installing aptdaemon, search it in synaptic and re-install all 4 listed packages.

Well, I have only one aptdaemon package in synaptics. And my update-manager is not working. Maybe . . . .

---

