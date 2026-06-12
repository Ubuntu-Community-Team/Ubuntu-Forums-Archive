---
title: "cinelerra 4.5 running as root ??"
date: 2014-03-18
forum: Multimedia Software
---

### Post by Flaggmann on 2014-03-18
I installed cinelerra 4.5 from source basicly following this procedure  [https://n1njahacks.wordpress.com/2013/03/09/installing-cinelerra-4-4-on-ubuntu-12-04/](https://n1njahacks.wordpress.com/2013/03/09/installing-cinelerra-4-4-on-ubuntu-12-04/)  found another link that listed prerequisites to install as well including libav and drm libraries also from source.

The program installed OK and appears to run fine, however it did not do the normal make install and add it to th menu. I created a launcher with code gksu /usr/bin/cinelerra to launch it. Unfortunately it is running as root and there are some troubles loading media files in due to permissions. Also I don't like the isea of having root run it. It was Ok to test and do an hour or so of fam on it but long term I would appreciate some pointers on getting it to run as a normal user or have a separate cinelerra system user run it so that the file permissions thing doesn't occur.

Thanx

---

### Post by lukeiamyourfather on 2014-03-18
The "gksu" in the command used to launch it means run as root. Why are you doing that?

---

### Post by Flaggmann on 2014-03-18
couldn't get it to run any other way as the pgm was /usr/bin/cinelerra with no permissions set or launchers created in the applications menu to just run it as a regualr user. I have purged the install and will try again.

---

### Post by lukeiamyourfather on 2014-03-18
You might need to change the permissions on the file to allow other users to execute it.

```
sudo chmod a+x /usr/bin/cinelerra
```

Then from a terminal you should be able to simply call "cinelerra" from there.

---

### Post by Flaggmann on 2014-03-18
FELL BACK TO VERS 2.2-CV  4.4 and 4.5 final output rendering unsatisfactory.

Thanks for assists

---

### Post by shaunthesheep on 2014-04-22
I have just installed Cinelerra CV 2.2 using this tutorial:

[http://handytutorial.com/install-cinelerra-in-ubuntu-12-04-12-10/](http://handytutorial.com/install-cinelerra-in-ubuntu-12-04-12-10/)

The only change I had to make was to substitute 
```

sudo apt-get install cinelerra-cv
```

for the now outdated:

```
sudo apt-get install cinelerra-av
```

I see that it is not the latest version and that there does not appear to be a simple, uncomplicated method of installing the latest v4.5. Why can't it be installed using the Ubuntu Software Centre?

I am just exploring Cinelerra for the first time. There doesn't appear to be a Cinelerra forum anywhere? Anyone know if there is one?

---

