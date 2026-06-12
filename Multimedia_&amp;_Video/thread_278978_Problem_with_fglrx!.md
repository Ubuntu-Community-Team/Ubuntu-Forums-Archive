---
title: "Problem with fglrx!"
date: 2006-10-17
forum: Multimedia &amp; Video
---

### Post by 25an on 2006-10-17
Hi!
I am runig Kubuntu but and when i try to enter System settings->Display to configure graphic i get following message.

The module Display could not be loaded.

The diagnostics is:

Possible reasons:
An error occured during you last KDE upgrade leaving an orphaned control module
You have old third part modules lying around

I have not upgraded KDE but the last thing i did before this error occurred was to remove 386 packages since i am running on P4 with hyper-threading.

I think that it might have something to do that I installed fglrx version 8.29.6 but the only package I could find was package for 386. I installed it and it worked just fine. But now when I removed all the 386 package the error occured, how dos this affect my system when I am running a Kernel for 686 but loading a 386 module?

If the fglrx is for 386 it probabliy needs the linux-header-386 package, right? Is there any other package that it needs then?

Should I remove the fglrx driver and reinstall the old driver or is it worth fixing?  


What command should I run if I would like to look at what modules is loaded? A commando like ls but for the kernel modules?

---

### Post by tonyr on 2006-10-20
Try re-installing package **kde-guidance**.  I was having the same problem,
and re-installing **kde-guidance** worked for me.

In a terminal do
```
sudo apt-get install --reinstall kde-guidance
```
or
```
sudo aptitude reinstall kde-guidance
```

---

