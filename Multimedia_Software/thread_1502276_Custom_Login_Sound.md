---
title: "Custom Login Sound"
date: 2010-06-05
forum: Multimedia Software
---

### Post by kajiotaku on 2010-06-05
Yes, I have searched.  I searched on the forums (found nothing somehow) and I searched with Google.  I have learned how to do it with earlier versions of Ubuntu, but not 10.04.

I want to change the login sound of Ubuntu 10.04 to a little clip of the intro of "All My Friends Are Dead".  I have already trimmed it and exported it as MP3 and OGG.  This is the part where I am having issues...

Where do I place the file(s) and how do I select them to be used for the login sound?

---

### Post by kajiotaku on 2010-06-05
Shameless bump.

---

### Post by kajiotaku on 2010-06-05
Self conscious bump.

---

### Post by kajiotaku on 2010-06-05
Is it impossible?

---

### Post by maddg3241 on 2010-06-06
What you will need: startup sound in ogg format.
 Step 1:
Go to System -> Preferences -> Starup Applications
Look for “GNOME Login Sound” in the list. If you don’t want to hear  anything at startup, uncheck this box.
If you want to change the sound, press Edit button. Then in the command  field you’ll see
 /usr/bin/canberra-gtk-play –id=”desktop-login” –description=”GNOME  Login”
 Change “desktop-login” to the name of the sound file you want,  without file extension.
Click Save and close the startup dialog.
 Step 2:
Now you have to copy this new sound (.ogg file) to
 /usr/share/sounds/ubuntu/stereo/
 You need  root permission to copy the file into this directory which  can be done by running nautilus as root.
 $sudo nautilus
 Then browse to that folder and paste the file there.
 Step 3:
Log out and login to listen to the new startup sound.

---

### Post by maddg3241 on 2010-06-06
easy as that

---

### Post by maddg3241 on 2010-06-07
remeber to mark as solved since the problem has been fixed

---

### Post by kajiotaku on 2010-06-07
> **maddg3241 said:**
> What you will need: startup sound in ogg format.
 Step 1:
Go to System -> Preferences -> Starup Applications
Look for “GNOME Login Sound” in the list. If you don’t want to hear  anything at startup, uncheck this box.
If you want to change the sound, press Edit button. Then in the command  field you’ll see
 /usr/bin/canberra-gtk-play –id=”desktop-login” –description=”GNOME  Login”
 Change “desktop-login” to the name of the sound file you want,  without file extension.
Click Save and close the startup dialog.
 Step 2:
Now you have to copy this new sound (.ogg file) to
 /usr/share/sounds/ubuntu/stereo/
 You need  root permission to copy the file into this directory which  can be done by running nautilus as root.
 $sudo nautilus
 Then browse to that folder and paste the file there.
 Step 3:
Log out and login to listen to the new startup sound.
Thank you so much x-x

---

