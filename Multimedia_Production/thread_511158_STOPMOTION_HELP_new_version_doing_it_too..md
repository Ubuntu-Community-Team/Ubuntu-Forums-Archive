---
title: "STOPMOTION HELP new version doing it too."
date: 2007-07-27
forum: Multimedia Production
---

### Post by toddbmobile on 2007-07-27
I went to use Stopmotion for the first time and as soon as i started it and tried to add an image (jpeg), the whole program closed. So i tried to open it back up and it opens for one second and closes. Over and over it keeps doing this. Just opening for one second and closing before i can even use my mouse to click anything. I've already restarted the computer and it keeps doing this.  This first version was from the package manager so I uninstalled it and downloaded the latest stopmotion (.deb) from the website. I also removed the hidden .stopmotion folder with no effect. What I get with the newest version is the program launches, but as soon as I try to import an image say a .jpg the program closes. Does anyone know of the fix? I see a lot of posts with this same problem, and all the current solutions do not work. Please help! Here below is what I get from the terminal window during the execution of the program:

Warning: Cannot connect to FAM
/bin/cp: target `/home/myfoldername/.stopmotion/tmp/tmp_0.jpg' is not a directory
QImage::scaled: Image is a null image
QPixmap::fromImage: Cannot convert a null image
Killed

When I get this either the program locks up, and you have to force quit it, or it just closes itself.:(

---

### Post by Rexbron! on 2007-07-27
Try removing the contents in the .stopmotion/tmp/ directory. It should at least load then.

---

### Post by toddbmobile on 2007-07-28
Thank you for the reply, regretfully the directory is empty. :(  No matter what I try it still closes as soon as I open it and try to import a .jpg, .gif etc...

---

### Post by Rexbron! on 2007-07-30
Ok, lets try a clean and reinstall. In at terminal window copy and paste:

```
sudo aptitude purge stopmotion && sudo aptitude install stopmotion 
```

---

### Post by toddbmobile on 2007-07-31
Thank you for the suggestion. I tried what you said and it got worse. Now as soon as I launch stopmotion it closes. So for I have tried installing and uninstalling "every which way but loose."

---

### Post by jimbean on 2007-09-27
i was having the same problem deleted said directory the {whole thing} then went to the stopmotion website and downloaded their latest build and now it works fine 
I was thinking that if i added to many files at once it overloaded the code of stopmotion ????

---

