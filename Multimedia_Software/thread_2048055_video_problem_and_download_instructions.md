---
title: "video problem and download instructions"
date: 2012-08-26
forum: Multimedia Software
---

### Post by chevyiron420 on 2012-08-26
I need some help! I cant play youtube video's, or others for that matter. I'm running ubuntu 10.04. I think from reading on the forum I have a problem with flash 11.2 and I think I need to downgrade. I have downloaded flash aid but i dont know how to install it or open it. Its in my downloads, but now what? Please walk me though what to do next.

---

### Post by user333 on 2012-08-26
Open Synaptic Package Manager and search for Adobe Flash. When you see the entry that looks like it is already installed(it should be flashplugin-installer), right-click it and click on 'Properties'. Then go into the 'Versions' tab, and select the lowest number or the one that says lucid. I'm not sure if this will work but it's worth a try.

---

### Post by chevyiron420 on 2012-08-26
> **user333 said:**
> Open Synaptic Package Manager and search for Adobe Flash. When you see the entry that looks like it is already installed(it should be flashplugin-installer), right-click it and click on 'Properties'. Then go into the 'Versions' tab, and select the lowest number or the one that says lucid. I'm not sure if this will work but it's worth a try.
  Well that took my firefox with it and now I have no browser at all. No way to connect with the internet.

---

### Post by user333 on 2012-08-26
What? That is really odd. I've used that method and it worked fine. Well, I guess re-installing FF would be the next step.

```
sudo apt-get install firefox
```

---

### Post by chevyiron420 on 2012-08-26
> **user333 said:**
> What? That is really odd. I've used that method and it worked fine. Well, I guess re-installing FF would be the next step.

```
sudo apt-get install firefox
```
That didn't work,I get a message, something like invalid operation, it just wont load firefox without the new flash.

---

### Post by user333 on 2012-08-27
Sounds like your software is messed up. I would try to install another browser through the software center so you can get by, revert any changes you made to flash in synaptic, and then update.

---

### Post by chevyiron420 on 2012-08-28
With great deal of help I was able to remove flash 11.2 and download 11.1, and install it. That took care of the problem.

---

