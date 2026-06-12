---
title: "Trying to use Shotwell with iPhone 6+ -- Says no photos/videos"
date: 2017-02-09
forum: Multimedia Software
---

### Post by shlap on 2017-02-09
Hi everyone, this is my first time taking Ubuntu for a spin and I gotta say I'm loving it so far, but there's one issue that's a showstopper for me.  

I'm trying to import photos using Shotwell.   When I open Shotwell, it shows my iPhone but when I click on camera or iPhone sections in Shotwell, neither of them show any photos.  I don't get any error message.  I clicked Trust on my iPhone and closed/re-opened Shotwell with no luck.  I also noticed that Rhythmbox doesn't show my iPhone at all, but Nautilus does. 

Running iOS 10.2.1 and Ubuntu 16.10.

Is there any other information I can provide to help troubleshoot this? 

Thanks!

---

### Post by shlap on 2017-02-20
Anyone?  I've tried reading photos off my iPhone on a laptop running 16.04 LTS and  16.10 with no luck :(  

Everything is working great on my Ubuntu machines except for this; would love to get it working.

---

### Post by shlap on 2017-03-16
Is anyone able to view photos/videos from their iOS 10 iPhone using Shotwell in 16.10 or 16.04?  I still haven't been able to figure this out.  Please help!

---

### Post by tobias.klaus on 2017-06-19
same problem here ... :(

---

### Post by oldfred on 2017-06-19
I just manually copy photos.
With newest iphone, I had to add the ppa.

I would think if you have it mounted then you can use shotwell to find that folder in the mount you create. But I just copy to folders that I want.

 [https://bugs.launchpad.net/ubuntu/+source/libimobiledevice/+bug/1623666](https://bugs.launchpad.net/ubuntu/+source/libimobiledevice/+bug/1623666)
[https://gist.github.com/samrocketman/70dff6ebb18004fc37dc5e33c259a0fc](https://gist.github.com/samrocketman/70dff6ebb18004fc37dc5e33c259a0fc)
[https://launchpad.net/~martin-salbaba/+archive/ubuntu/ppa+libimobiledevice](https://launchpad.net/~martin-salbaba/+archive/ubuntu/ppa+libimobiledevice)
sudo add-apt-repository ppa:martin-salbaba/ppa+libimobiledevice 
   iphone
  sudo mkdir /mnt/iPhone
fred@Z170N:~$ sudo chown -R $USER:$USER /mnt/iPhone 
fred@Z170N:~$ sudo chmod -R a+rwX,o-w /mnt/iPhone 
   idevicepair pair
Info 
ideviceinfo -d
ifuse /mnt/iPhone/
ls  /mnt/iPhone
to unmount:
fusermount -u /mnt/iPhone
idevicepair unpair
SUCCESS: Unpaired with device 78cf71cea...
[https://askubuntu.com/questions/909988/i-connect-my-iphone-5-ios-10-3-1-but-my-ubuntu-16-04-doesnt-seem-to-detect-it/910094#910094](https://askubuntu.com/questions/909988/i-connect-my-iphone-5-ios-10-3-1-but-my-ubuntu-16-04-doesnt-seem-to-detect-it/910094#910094)

---

### Post by sp40140 on 2017-06-20
can't specifically speak for shotwell. 
I usually run windows in VM just for MS Office and iOS devices management.
On rare occasions, I do use nautilus to copy photos manually.
If some application doesn't work with you iOS device, it's best for your health to avoid trying to fix it. It's a hit or miss with lots and lots of misses.
Either go back to windows (sadly) or run windows VM for these occasions.

---

