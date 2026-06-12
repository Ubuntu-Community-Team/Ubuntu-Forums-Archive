---
title: "OpenGL -&gt; No switching after update"
date: 2011-04-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tembares on 2011-04-26
Hello,

I am trying to set the permissions right to switch between my two cards: Intel i915 and ATI.

It worked before, but I cannot
```
echo DIS > (sudo) cat /sys/kernel/debug/vgaswitcheroo/switch
bash: sudo: Permission denied
```
```
echo ON > sudo cat /sys/kernel/debug/vgaswitcheroo/switch
bash: sudo: Permission denied

```
anymore (the 'sudo' between () is optional, could not do it with or without 'sudo').

```
cat /sys/kernel/debug/vgaswitcheroo/switch
```
shows me a permission error.

```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
```
shows me the output as usual.

This all happend after an update from OpenGL.

Settings/permissions:
bla:/usr/local/bin$ sudo ls -laF /sys/kernel/debug/vgaswitcheroo/switch
-rw-r--r-- 1 root plugdev 0 2011-04-26 20:59 /sys/kernel/debug/vgaswitcheroo/switch

bla:/usr/local/bin$ ls -laF switch
-rwxr-xr-x 1 root username 563 2011-04-20 19:41 switch*

Thank you in advance.

---

### Post by chadmerkert on 2011-04-26
Hey Tembares,

Try this replacing any $name in both commands with your username:
```
sudo su
chown -R $name:$name /sys/kernel/debug
chown $name:$name /sys/kernel/debug/vgaswitcheroo/switch
exit

```
Then try the cat and echo again. Hope this works!

---

### Post by tembares on 2011-04-26
> **chadmerkert said:**
> Hey Tembares,

Try this replacing any $name in both commands with your username:
```
sudo su
chown -R $name:$name /sys/kernel/debug
chown $name:$name /sys/kernel/debug/vgaswitcheroo/switch
exit

```
Then try the cat and echo again. Hope this works!

That was quick and it worked!
Let's implement this in the script: [http://ubuntuforums.org/showthread.php?t=1716403]("http://ubuntuforums.org/showthread.php?t=1716403")

---

### Post by chadmerkert on 2011-04-26
That already is in the script... it should have been placed into your /etc/gdm/PostLogin/Default file! :D Check to make sure these commands are in there. If your not sure, post the output of cat /etc/gdm/PostLogin/Default

If they are not in there, these permissions may be lost on reboot.

---

### Post by tembares on 2011-04-26
Yep, it was gone after reboot.
Default:
```
bla:# cat /etc/gdm/PostLogin/Default
#!/bin/sh
chown -R *username*:*username* /sys/kernel/debug
chown *username*:*username* /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

This makes it more strange.
```
ls -laF *folders/filename*
```
shows that the group:user settings are root:root.

---

### Post by tembares on 2011-04-26
The issue was that I enabled auto logon.
With auto logon set on 2 seconds with the possibility to switch user before, this problem has been solved.

---

### Post by alexmurray on 2011-04-27
Making /sys/kernel/debug owned by your user basically means you've opened a significant security hole in your machine (since debugfs exposes a bunch of interfaces to writing to kernel memory) - [there is a reason]("https://launchpad.net/ubuntu/+source/mountall/2.22") it is owned by root in the first place. I really wouldn't do that. There are other ways to achieve this such as a setuid shell script which contains the

```
echo XXX > /sys/kernel/debug/vgaswitcheroo/switch

```
stuff.

---

### Post by chadmerkert on 2011-04-27
Alexmurray,

If it opens up a security hole, I would like to close it, but I can't figure out how to give my user account permission to access just the /sys/kernel/debug/vgaswitcheroo folder. Without access to this folder, my laptop is must less usable! Can you please tell me how I can give my username permission to edit this file,(without sudo being required) without opening up this security hole? I have tried to chown just the vgaswitcheroo folder, but that still gives me permission denied. Thanks for your help!

---

### Post by chadmerkert on 2011-04-27
Alexmurray, I'm no professional at Linux security, so I would like to get your input on this. I found a way to use the /sys/kernel/debug/vgaswitcheroo/switch file without using chown on /sys/kernel/debug/

I have ```
chmod 705 /sys/kernel/debug/ 
```Which if I'm correct will only give read and execute permissions to the debug folder
Then I ```
chown -R username:username /sys/kernel/debug/vgaswitcheroo
```

This way, root is the owner of the debug folder, and other users can only read and execute from the debug folder, and the username selected can read/write/execute the vgaswitcheroo folder.

I think this should make this much more secure, and it seems to work perfectly. Would you agree that this makes it more secure? Thanks for your input.

---

