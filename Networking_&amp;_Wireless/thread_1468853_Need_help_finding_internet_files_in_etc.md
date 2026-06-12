---
title: "Need help finding internet files in /etc/"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by RazirFyre on 2010-05-01
Ok, so the problem I have is that I can't update anything at all, my update manager isn't working because I created a few internet files in my /etc/ somewhere so that I could use the internet through a wingate network and now I need to get rid of those files because I'm on a direct connection now.  I'm running Intrepid Ibex.  If anybody has any clue as to what I can to do fix this, I'd be very grateful.

---

### Post by chili555 on 2010-05-01
I know nothing about wingate networks, but you could probably find out which files you edited with:```
history | grep /etc
```We can help you to restore them to default.

---

### Post by RazirFyre on 2010-05-02
If you could help me, that'd be wonderful.  I have eight updates that I've been needing to install for the past week or so and it's making me frantic.

---

### Post by chili555 on 2010-05-02
> **RazirFyre said:**
> If you could help me, that'd be wonderful.  I have eight updates that I've been needing to install for the past week or so and it's making me frantic.Glad to. Do you have any actual data? Did you try my command? Do you now know the files you modified?

---

### Post by RazirFyre on 2010-05-02
This is what I get after running your command.  

> razir@razir-desktop:~$ history | grep /etc 
   23  sudo gedit /etc/apt/sources.list
   38  history | grep /etc
   39  history | grep /etc 
razir@razir-desktop:~$ 


---

### Post by chili555 on 2010-05-02
I don't see much there. Since history is only 39 items long, please post the whole thing.

Editing your sources.list generally allows you to download packages which are not in the default Ubuntu repositories; it should do no real harm. If you want to post it here, we'll be glad to sanitize it for you.

---

### Post by RazirFyre on 2010-05-02
How do I expand it?  What I posted is all that shows up in my Terminal.

---

### Post by tad1073 on 2010-05-02
try looking /etc/networks/ or /etc/hosts

---

### Post by chili555 on 2010-05-02
> **RazirFyre said:**
> How do I expand it?  What I posted is all that shows up in my Terminal.Please do:```
history
```Copy and paste everything into your reply.

---

