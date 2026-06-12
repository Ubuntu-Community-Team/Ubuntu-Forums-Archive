---
title: "Unable to add ANY PPA"
date: 2019-04-11
forum: MINT
---

### Post by salil.work on 2019-04-11
[COLOR=#333333][FONT=&amp]Hello,[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I am running Linux Mint 19.1 Tessa (base ubuntu 18.04) on my laptop. I am unable to add ANY PPA to the repository (for example: [/FONT][/COLOR]sudo add-apt-repository ppa:geany-dev/ppa[COLOR=#333333][FONT=&amp]). Whenever I try to add a PPA to the repository, I end up with a message:[/FONT][/COLOR]
gpg: keyserver receive failed: Server indicated a failure

I am not sure whether the problem is related to Linux Mint or to its base which is Ubuntu 18.04. Hence I am posting my problem in this forum.
[COLOR=#333333][FONT=&amp]Please note that I have been able to add the required repositories on my second laptop which also runs Linux Mint 19.1 Tessa.[/FONT][/COLOR]
 
[COLOR=#333333][FONT=&amp]Any help would be greatly appreciated.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Thank you[/FONT][/COLOR]

---

### Post by Frogs Hair on 2019-04-11
Moved to [I]Mint.

[/I]
I don't see any packages for Bionic listed, the newest appears to be for 17.10*. *There is a new version for 14.04 which reaches EOL soon. [https://launchpad.net/~geany-dev/+archive/ubuntu/ppa](https://launchpad.net/~geany-dev/+archive/ubuntu/ppa)

---

### Post by Rubi1200 on 2019-04-11
Hi and welcome to the forums :-)

Please post the output of this command:

```
cat /etc/resolv.conf
```

Thanks.

---

### Post by salil.work on 2019-04-11
Thanks for the reply. But I was able to install Geany (1.34) on another machine which is running Mint 19.1 using the PPA. The problem is not limited to a single package. I get the same error whenever I try to add a PPA using [COLOR=#333333]sudo add-apt-repository[/COLOR]. Here is another example ([COLOR=#333333]sudo add-apt-repository ppa:fenics-packages/fenics). I am able to install Fenics on my "other" machine but not my laptop.[/COLOR]

---

### Post by Rubi1200 on 2019-04-11
Are both machines connected to the same network and have exactly the same network settings?

Check /etc/resolv.conf because gpg requires an entry in that file in order to work correctly (at least according to this post [https://www.reddit.com/r/archlinux/comments/6v5xlg/gpg_server_indicated_a_failure/](https://www.reddit.com/r/archlinux/comments/6v5xlg/gpg_server_indicated_a_failure/))

Another user resolved it here: [https://unix.stackexchange.com/questions/399027/gpg-keyserver-receive-failed-server-indicated-a-failure](https://unix.stackexchange.com/questions/399027/gpg-keyserver-receive-failed-server-indicated-a-failure) and [https://prnt.sc/nalecj](https://prnt.sc/nalecj)

Hope this helps.

---

### Post by salil.work on 2019-04-11
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Please post the output of this command:

```
cat /etc/resolv.conf
```

Thanks.
Thanks for your reply. The output of the command is:
nameserver 127.0.0.53
options edns0

---

### Post by salil.work on 2019-04-11
> **Rubi1200 said:**
> Are both machines connected to the same network and have exactly the same network settings?

Check /etc/resolv.conf because gpg requires an entry in that file in order to work correctly (at least according to this post [https://www.reddit.com/r/archlinux/comments/6v5xlg/gpg_server_indicated_a_failure/](https://www.reddit.com/r/archlinux/comments/6v5xlg/gpg_server_indicated_a_failure/))

Another user resolved it here: [https://unix.stackexchange.com/questions/399027/gpg-keyserver-receive-failed-server-indicated-a-failure](https://unix.stackexchange.com/questions/399027/gpg-keyserver-receive-failed-server-indicated-a-failure) and [https://prnt.sc/nalecj](https://prnt.sc/nalecj)

Hope this helps.

The machines are connected to the same network. The machine on which I do not have a problem has a wired network connection while the one which is giving me problems has a wireless network connection.

---

