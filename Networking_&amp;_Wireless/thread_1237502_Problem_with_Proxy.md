---
title: "Problem with Proxy"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by EliteLegend on 2009-08-11
Lately, I am observing this problem and am not sure if I'm the only one.

Problem:
I setup a proxy using Systems->Preferences->Network Proxy
Click on Apply System-Wide
Everything works
Using the same procedure I remove the proxy and click on Apply System-Wide, nothing works. I mean I can get the browser running by setting the proxy manually but anything that I do using the shell and or perhaps the Update Manager does not work.

I'm thinking this is a bug and was hoping if anyone solved it... Its getting really annoying to restart Ubuntu everytime I change my proxy. Any help is appreciated. Thanks

---

### Post by giggins on 2009-08-11
Did you close your browser and re-open it after making the proxy settings?

Also, try opening a new terminal, and type:

```
export | grep http_proxy
```

Do you see anything returned after you remove your proxy settings?

---

### Post by EliteLegend on 2009-08-11
Thanks for the reply...

Yes... I still see that the http_proxy variable is set to use my proxy... Ah... this looks like the one creating a problem... I removed the proxy and clicked "Apply System-wide" but it doesn't show me any change...

---

### Post by EliteLegend on 2009-08-12
Anyone? :(

---

### Post by giggins on 2009-08-12
Sorry... Nothing really to say; I can't replicate the issue. Are you using Ubuntu 9.04 i386?

---

### Post by EliteLegend on 2009-08-12
Yes... (I have see an almost similar issue in another post:

```
https://bugs.launchpad.net/ubuntu/+source/wget/+bug/232469
```

I tried resolving it using the steps there but it still persists.)

If this is the case, considering that the variable is not being set, is there a way I can do this manually at least? I don't mind running a shell script or some other manual procedure as long as it can fix my problem without asking me to restart.

---

### Post by giggins on 2009-08-13
There is a way to manually set your proxy settings. When you open a terminal, type:

```
export http_proxy=''
```

This unsets your proxy for the terminal you have open. This is only temporary, meaning next time you run a new login shell (run su -l, or launch a new terminal) your proxy settings will be the system settings. This change will not affect your web browser (unless you're running w3m...). Firefox has a way to manually set its proxy config through "Edit" -> "Preferences" -> "Advanced" -> "Network" -> "Settings...".

To set your terminal proxy settings more permanently, add it to one of bash's configs. "/etc/bashrc" sets it for all users, while "~/.bashrc" sets it for just your user.

---

