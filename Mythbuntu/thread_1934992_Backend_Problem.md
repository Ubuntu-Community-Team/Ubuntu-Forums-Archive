---
title: "Backend Problem"
date: 2012-03-03
forum: Mythbuntu
---

### Post by Perpetualnoob on 2012-03-03
I recently installed Mythbuntu on a Zotac Zbox Nano. The install went good and it booted just fine to complete the install. Now every time I boot/reboot it comes up with the message "Could not connect to the backend server. Is it running? Is the IP address set for it in mythtv-setup correct? I click ok to clear that message and try to exit to the desktop and I get the message "Do you really want to exit Mythtv?" I click "Yes, exit now." and the computer freezes. I forgot to mention that I'm running the front and back end on the same computer. I have very little experience with Linux based systems so have some patience with me. Thanks. I found it's not freezing up it just takes a while to exit.

---

### Post by klc5555 on 2012-03-03
> **Perpetualnoob said:**
> I recently installed Mythbuntu on a Zotac Zbox Nano. The install went good and it booted just fine to complete the install. Now every time I boot/reboot it comes up with the message "Could not connect to the backend server. Is it running? Is the IP address set for it in mythtv-setup correct? I click ok to clear that message and try to exit to the desktop and I get the message "Do you really want to exit Mythtv?" I click "Yes, exit now." and the computer freezes. I forgot to mention that I'm running the front and back end on the same computer. I have very little experience with Linux based systems so have some patience with me. Thanks. I found it's not freezing up it just takes a while to exit.

Well, on a brand-new install the mythtv backend probably in fact is not running. It won't start on its own at boot until you have set it up. You can set it up via the Control Centre from within Mythtv, or, having already exited to the desktop, by going into the mythbackend setup from the Xfce4 menu or by running sudo mythtv-setup from a terminal.

---

### Post by nickrout on 2012-03-03
> **klc5555 said:**
> Well, on a brand-new install the mythtv backend probably in fact is not running. It won't start on its own at boot until you have set it up. You can set it up via the Control Centre from within Mythtv, or, having already exited to the desktop, by going into the mythbackend setup from the Xfce4 menu or by running sudo mythtv-setup from a terminal.

Actually I believe that like most daemons in buntuland, it does start by default once installed.

Anyway it is easy to check by running ```
ps ax|grep back
```

---

### Post by Perpetualnoob on 2012-03-04
I ran ps ax|grep back. I'm not sure what I should be looking for.

---

### Post by nickrout on 2012-03-04
you are (obviously) looking for mythbackend running, like here where mine IS running:> nick@media:~$ ps ax|grep back
 1332 ?        Sl    43:12 /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log --user mythtv
 3995 pts/3    S+     0:00 grep --color=auto back

---

### Post by Perpetualnoob on 2012-03-04
This is what I have:
 
1242 tty Ss+ 0:43/usr/bin/x:0 -auth/var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
3187 pts/0 S+ 0:00grep --color=autoback

---

### Post by nickrout on 2012-03-04
start the backend then!

```
sudo start mythtv-backend
```

---

### Post by Perpetualnoob on 2012-03-04
When I run sudo start mythtv-backend it comes up with:
mythtv-backend start/running, process 12332
but if I enter sudo service mythtv-backend status it tells me mythtv-backend/ stop waiting and if I try to use mythtv it comes up with the original message that I originally had. Doesn't seem like it wants to keep running.

---

### Post by nickrout on 2012-03-04
> **Perpetualnoob said:**
> When I run sudo start mythtv-backend it comes up with:
mythtv-backend start/running, process 12332
but if I enter sudo service mythtv-backend status it tells me mythtv-backend/ stop waiting and if I try to use mythtv it comes up with the original message that I originally had. Doesn't seem like it wants to keep running.

after you have started it, what does the ps command show?

what does the log file /var/log/mythtv/mythbackend.log tell you?

---

### Post by Perpetualnoob on 2012-03-04
when I ran ps -e the only thing I could find was:
3371 ? 00:00:00 backend_helper.
11937 pts/2 00:00:00 frontend
 
When I tried to look for the log file it said permission denied.

---

### Post by Perpetualnoob on 2012-03-04
Nick, I'd like to thank you for your help. I don't know enough about Linux or code and I don't want to waste your time or mine anymore. So I'm going to go with plan B and aviod these problems. Thanks again for you time.

---

### Post by nickrout on 2012-03-05
you give up too easily, there is plenty more help available!

But, of course, good luck with planB

(If Plan B is win MCE, you'll be back LOL)

---

### Post by Perpetualnoob on 2012-03-05
Usually I figure out problems like this on my own but I'm like a fish out of water with code. If you don't mind working with me I'll keep going but I don't want to drag you down into the abyss with me.

---

