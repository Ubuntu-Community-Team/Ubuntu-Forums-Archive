---
title: "Cant enter IMDB numbers in 9.04"
date: 2009-05-23
forum: Mythbuntu
---

### Post by mark467 on 2009-05-23
I have a fresh install of 9.04 and seem to have everything else working except I cant manually enter IMDB #'s.
In video manager I try to use the menu and select manually enter I go back to main screen with just a black box that says Enter IMDB # but it will not accept input.

---

### Post by tgm4883 on 2009-05-23
Known issue, please search next time.  Thanks
[http://ubuntuforums.org/showthread.php?t=1101527](http://ubuntuforums.org/showthread.php?t=1101527)

---

### Post by mark467 on 2009-05-25
I did search. I did try that and the box disappeared from the main screen but still wont let me enter a number. using the following makes the box disappear in all themes but does not allow manual entry still.

sudo find /usr/share/mythtv/themes/ -name "video-ui.xml" -print | xargs sudo sed -i 's/enterimdb/entertmdb/g'

---

### Post by laffinet on 2009-05-25
I have the same problem. I tried

```
sudo find /usr/share/mythtv/themes/ -name "video-ui.xml" -print | xargs sudo sed -i 's/enterimdb/entertmdb/g' 
```

But that didn't seem to work. Must have gotten something wrong there. 

I then manually edited the video-ui.xml file (changing enterimdb to entertmdb) but the box doesn't disappear, nor can I enter the imdb number manually.

---

### Post by mark467 on 2009-06-29
anybody? the above does not work for me either

---

### Post by gwagchunks on 2009-07-11
> **laffinet said:**
> I have the same problem. I tried

```
sudo find /usr/share/mythtv/themes/ -name "video-ui.xml" -print | xargs sudo sed -i 's/enterimdb/entertmdb/g' 
```

But that didn't seem to work. Must have gotten something wrong there. 

I then manually edited the video-ui.xml file (changing enterimdb to entertmdb) but the box doesn't disappear, nor can I enter the imdb number manually.

Strange, I had the same problem and tried the code and it worked for me (so far). The imdg box is not there in video manager and it comes up input capable when I press I or M.

---

