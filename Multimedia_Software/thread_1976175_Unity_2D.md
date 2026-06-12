---
title: "Unity 2D"
date: 2012-05-08
forum: Multimedia Software
---

### Post by gabmuks on 2012-05-08
Hello and good day.

MyUnity says that I have Unity 2D.
Does that refer to my computer graphics?
If so, then is it possible for me to change to Unity 3D?

Thank you for your time.

Pat L.

---

### Post by JRV on 2012-05-08
This command will tell you if Unity 3D is supported on your graphics card:```
/usr/lib/nux/unity_support_test -p
```

If it is supported click on the Ubuntu symbol next to your name on the login screen and select Ubuntu.

---

### Post by gabmuks on 2012-05-10
Thank you for kind reply.

I did as you suggested. (/usr/lib/nux/unity_support_test -p)
The results say that I have 3D Nividia running. (version 295.49) Also my screensaver runs 3D images.
But only Unity 2D will run with Ubuntu 12.04.

I did go to the "Log in" screen and clicked on the Ubuntu icon
and then clicked on Unity. This caused my screen to go completely
blank and lock up. Not knowing what to do, I completely
re-installed Ubuntu 12.04 which resulted in losing 10 years
worth of saved family photos. (My mistake)

Anyway I still don't understand why Unity will only work in 2D.

Does anyone have a solution?
Thank you for your time.

Pat L.

---

### Post by TBABill on 2012-05-10
The reinstall was completely unnecessary. All you had to do was restart, select 2D at the login screen, and revert back to what you were using previously. I know it is hindsight at this point, but perhaps asking for help before assuming the system cannot be fixed will help prevent such a catastrophic loss of data in the future. I am genuinely sorry you lost so many memories and other data. In the future I'd recommend some form of external storage as a regular backup of your important data to help prevent losses like this.
 
I'm not sure if you are aware, but with the liveDVD or USB, you can fire up the system and mount the drive where data is held, then copy it to another drive. That way if something prevents booting, you still have a way to recover files.

---

### Post by gabmuks on 2012-05-10
Thanks much TBABill!

Yes, actually I did have all my photos
and documents on an external drive and
was sorting through...cleaning up some old files,
emptying the external drive and then I was
going to put the revised files and folders
back on to the external drive. But before I got them
transferred back to the ext. drive, my wife found
something more important for me to do.
I forgot all about the photos and documents until
the next day after the crash. I also figured out how to
go back to Unity 2D after the blackout.
But way too late I am sorry to say.
Anyway, I learned a good lesson the hard way (as usual for me).

Thank you for kind reply.

Pat L.

But does anyone know why 3D Unity wont work with my Ubuntu 12.04?

Thank you for your time.

---

### Post by TBABill on 2012-05-10
I believe there is a bug filed already related to nVidia cards (at least some of them) not working in 3D. Launchpad would be a good place to find them listed and you can join and add yourself as another user impacted.

---

### Post by TBABill on 2012-05-10
One more thought on that. Have you tried getting the latest driver directly from nVidia and trying it to see if it works in 3D? Could be a package issue with the Ubuntu version in the repos and not a broken driver with Unity 3D issue.

---

### Post by gabmuks on 2012-05-10
Yes. I have the latest Nividia driver.
I believe it is version 295.49 according to the Unixmen website.
And the /usr/lib/nux/unity_support_test -p command says that I have
3D capabilities.

---

