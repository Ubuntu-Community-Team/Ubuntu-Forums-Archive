---
title: "Boxee 64bit?"
date: 2009-10-19
forum: Multimedia Software
---

### Post by x C0MMAND0 x on 2009-10-19
Anybody know where a version of Boxee 64bit exists?  It is such an amazing program...

---

### Post by vinutux on 2009-10-19
Don't know about Boxee.. But i think XMBC have seperate 64 and 32 versions...

---

### Post by x C0MMAND0 x on 2009-10-20
It does, but Boxee has so many more features than XBMC, and I'd really hate to have to install a different version on my current media PC just to get it to work...

There's no way to downgrade from 64 to 32 is there?  Probably a dumb question...

---

### Post by silverdulcet on 2009-10-21
> **x C0MMAND0 x said:**
> It does, but Boxee has so many more features than XBMC, and I'd really hate to have to install a different version on my current media PC just to get it to work...

There's no way to downgrade from 64 to 32 is there?  Probably a dumb question...

See my post here for a painless way to get boxee running on Ubuntu 64-bit. I wrote the post in response to getting it to work on Mythbuntu 64-bit but the script will work just as well for Ubuntu. 

[http://ubuntuforums.org/showpost.php?p=7943304&postcount=9]("http://ubuntuforums.org/showpost.php?p=7943304&postcount=9")

---

### Post by x C0MMAND0 x on 2009-10-21
It's downloading now...I'm excited!

---

### Post by x C0MMAND0 x on 2009-10-21
K...so it downloaded and appears in my Applications > Sound & Video list, but when I click on it it doesn't load.  Is there a way to uninstall what I currently have and re-run the script?

---

### Post by silverdulcet on 2009-10-21
> **x C0MMAND0 x said:**
> K...so it downloaded and appears in my Applications > Sound & Video list, but when I click on it it doesn't load.  Is there a way to uninstall what I currently have and re-run the script?

Before uninstalling try running this from a Terminal and see if there are any errors. Then post them here.
```
/opt/boxee/run-boxee-desktop
```

You could also try to rerun getlibs to make sure you aren't missing any of the 32-bit libs that boxee requries by running this from the terminal.
```
getlibs /opt/boxee/Boxee
```

To uninstall the package just run from the Terminal
```
sudo dpkg -r boxee 
```

---

### Post by x C0MMAND0 x on 2009-10-22
Running the 32bit library install took care of it.  Thank you SO much, I really appreciate it.

---

