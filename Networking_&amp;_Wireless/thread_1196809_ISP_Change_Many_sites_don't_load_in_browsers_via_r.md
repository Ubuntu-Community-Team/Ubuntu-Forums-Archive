---
title: "ISP Change: Many sites don't load in browsers via router,but work in XP or w/o router"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by External on 2009-06-25
Dear fellow Ubuntu users,

I'm having some weird networking problem that truly boggles me, and which actually renders my home working impossible.
I used to have a slow DSL connection, but this Monday I switched ISP's and now have a new connection that is independent of the phone line (and unlike my old DSL connection requires no modem), but just as before, the access is shared via the same router among 3 computers. These are as follows:

1. One connects to the router via cable and runs Windows XP,
2. One connects via wireless and runs XP and Fedora in dual boot 
3. The third one (my own) connects via wireless / cable (I tried both) and runs Ubuntu Intrepid.

Sometime after the new connection was installed I realized that Firefox 3.0 on my Ubuntu Intrepid does not open many sites. First I thought the ISP might have some blocking on these, but since they are totally independent (and the nature of their content isn't interlinked either) it wouldn't have made sense. Then I also realized that the other 2 computers can open all of these websites in WinXP in Firefox and Opera, as well.

These are the things I tried - **to no avail**:

1. Tried connecting to the router via cable, and then wireless.
2. Reset the router.
3. Reset the router and restored factory settings (only added the username & pass of the new ISP account).
4. Tried opening the sites from an Ubuntu Intrepid Live CD (in Firefox)
5. Tried opening the sites from an Ubuntu Jaunty Live CD (in Firefox)
6. Tried opening the sites from a Kubuntu Intrepid Live CD (in Konqueror)

_Then:_ 
**A.** Disconnected the cable from the router and connected it straight to my computer and set up pppoeconf in terminal (with default choices): With that ***everything worked perfectly***.
**B.** Reset the router (and entered the account data of my old account), plugged it to my old DSL modem, tried connecting to the router first via cable, then wireless. With that ***everything worked perfectly*** (both ways).

**So it seems that the _old_ ISP account works with my Ubuntu via my router (no matter which way I connect) but my _new_ ISP connection only does so without the router.**

I tried these (the latter one for wireless) separately too just to make sure, but the problem persisted:

```
sudo ifconfig eth0 mtu 1492
sudo ifconfig eth1 mtu 1492
```


[i]Some of the sites I can't access:
[http://en-us.www.mozilla.com/en-US/firefox/central/](http://en-us.www.mozilla.com/en-US/firefox/central/)
[http://www.ikea.com/](http://www.ikea.com/)
[http://www.facebook.com/](http://www.facebook.com/)
[http://noscript.net/](http://noscript.net/) (can access only the header)[/i]
[www.ati.com](www.ati.com)
[www.nvidia.com](www.nvidia.com)


At this moment, for a short period of time both my old and new internet subscriptions work, so I could test them both.

[b]If you have any ideas, and some time, please help me find a solution.
Thanks a lot in advance![/b]

Best regards,
External

---

### Post by jhannah on 2009-06-25
Is it correct to say that the problem site you are trying to connect to are always an issue with your new setup? That is, they never work correctly?

I think it might be worth running MTR to see what the path to some of these sites looks like. You can install and run MTR with the below command to get results you can paste:

```

sudo aptitude install mtr
mtr -c 5 -r 163.181.249.208

```

163.181.249.208 is the IP address for ati.com but any other site/IP that you are having problems reaching should be fine to use. To compare, can you also try running this MTR against a site that does work fine?

Lastly, what type of internet connection and router/modem do you have with your new Internet connection? It sounds like you are using PPPoE between your router and your modem but I wanted to make sure that was correct.

---

### Post by External on 2009-06-25
Jon,

Thank you for your reply, I appreciate your time and help.

It is absolutely correct to say that it's always the same sites that never work with the new setup via my router, regardless of what distro I use (I tried Intrepid, the one I have installed, the live cd and the Jaunty live CDs for both Ubuntu and Kubuntu), and regardless of what browser I use. Also the sites that work do work consistently.

**Update**: I tried reaching the problem sites on Fedora 9 (Firefox) on one of the other machines and I have exactly the same problem _with exactly the same sites_, so this seems to me a general Linux issue, and not an Ubuntu-related one.

My router is an Edimax BR6204Wg and it is the one I used with both setups.
My modem is a Dialcom ADSL Bridge (model 1600), and only my old DSL connection required it, the new connection does not. It is a microwave internet access, the tower is on the roof of the 11 story house I live in, and only a bare UTP cable enters my flat.

And yes, I am using **PPPoE**.

I installed **mtr** and this is the path it got for the ati.com site you gave the IP for **(NOT working: 163.181.249.208**).

```

HOST: dell                        Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.2.1                   0.0%     5    4.8   2.7   1.5   4.8   1.3
  2. 192.168.3.254                 0.0%     5    7.7   4.7   2.7   7.7   2.1
  3. ???                          100.0     5    0.0   0.0   0.0   0.0   0.0
  4. 213.253.204.141               0.0%     5   20.7  10.2   5.0  20.7   6.3
  5. xe-2-0-0.bix-p2.invitel.net   0.0%     5    9.6   9.9   6.1  17.8   4.7
  6. ge-7-0-0.bud4core1.invitel.n  0.0%     5   14.0   8.2   4.9  14.0   3.5
  7. ge-6-1-0.bud2core1.pantel.ne  0.0%     5    9.4   7.0   5.0   9.7   2.3
  8. gigabitethernet2-0.gw9.fft4.  0.0%     5   44.5  28.5  21.9  44.5   9.1
  9. so-2-0-0.cr1.fft1.alter.net   0.0%     5   27.9  26.4  23.3  31.6   3.4
 10. so-0-3-0.xt1.fft1.alter.net   0.0%     5   23.9  24.4  23.2  25.8   1.1
 11. ge-0-1-0.il1.dca4.alter.net   0.0%     5  114.3 113.3 108.8 120.6   4.7
 12. 0.so-7-0-0.il3.dca6.alter.ne  0.0%     5  110.7 122.8 110.6 167.3  24.9
 13. 0.so-6-0-0.xl1.aus4.alter.ne  0.0%     5  151.8 176.0 149.9 217.3  27.4
 14. pos6-0.gw2.aus4.alter.net    20.0%     5  150.4 152.5 147.7 163.8   7.6
 15. amd-gw.customer.alter.net     0.0%     5  150.7 150.7 149.7 153.4   1.6
 16. 163.181.252.94                0.0%     5  173.9 160.4 149.1 173.9   9.0
 17. 163.181.251.101               0.0%     5  152.2 169.2 151.8 228.8  33.4
 18. 163.181.249.17               20.0%     5  156.1 155.5 148.6 167.2   8.4
 19. 163.181.249.208              20.0%     5  153.3 153.4 152.3 155.5   1.4
```

As opposed to a site which is **working flawlessly (ubuntu.com: 91.189.94.156)**
```

HOST: dell                        Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.2.1                   0.0%     5   12.8   3.9   1.7  12.8   5.0
  2. 192.168.3.254                 0.0%     5   18.3   8.9   3.7  18.3   6.3
  3. net-80-253-180-57.beltav.hu  20.0%     5    9.8   9.8   9.8   9.8   0.0
  4. 213.253.204.141               0.0%     5   20.0  11.5   5.4  20.0   6.0
  5. xe-2-0-0.info-p2.invitel.net  0.0%     5    6.1   8.6   6.1  14.3   3.3
  6. ge-7-0-0.bud2core1.invitel.n  0.0%     5    6.2   6.9   5.3   8.8   1.4
  7. xe-10-0-0-209.bud-001-score-  0.0%     5   25.2  19.4   6.0  32.1  12.5
  8. ae2-0.prg-001-score-2-re0.in  0.0%     5   29.4  34.9  20.7  56.8  15.6
  9. ae0-0.prg-001-score-1-re0.in  0.0%     5   14.9  17.2  12.4  29.1   6.8
 10. ae2-0.fra-006-score-2-re0.in  0.0%     5   23.8  26.6  22.1  39.7   7.3
 11. ge0-1-0-cr0.ixf.de.as6908.ne  0.0%     5   31.8  65.3  31.8 190.8  70.2
 12. te1-4-3503-cr0.tch.uk.as6908  0.0%     5  171.6 137.3  57.5 185.3  51.6
 13. canonical-gw.datahop.net      0.0%     5   40.7  40.7  35.8  46.4   4.1
 14. gw0-0-gr.canonical.com        0.0%     5   38.1  49.6  38.1  82.6  18.6
 15. vostok.canonical.com          0.0%     5   36.7  41.5  36.7  51.3   5.9
```

If it matters for interpretation, my new ISP is called "beltav", the old one is "invitel", and the latter is a relatively huge telecommunication company, which might be the reason why their name eventually pops up in both paths. However, I'm only guessing.

---

### Post by External on 2009-06-26
OK, so I contacted my new ISP about the problem, and the network admin raised the MTU value between their local router and mine to **1492**, which is the value used by ADSL connections. (Remember, that I am using microwave internet access.) Nothing changed so far, but I sent him the settings for 

ifconfig
route
cat /etc/resolv.conf

However, if anyone has any ideas, you'd make me happy if you shared them.

---

### Post by Gen2ly on 2009-06-26
You might want to look at this thread:

[http://bbs.archlinux.org/viewtopic.php?pid=575135](http://bbs.archlinux.org/viewtopic.php?pid=575135)

And look at Bogart's suggestion, somerouters have problems unless you disable scaling.

---

### Post by External on 2009-06-27
Gent2ly, thanks for your reply.

**Unfortunately**, the advice in the referred post doesn't seem to have solved the problem. I copied the line **net.ipv4.tcp_window_scaling = 0** to **/etc/sysctl.conf**, but no success, a portion of sites is still inaccessable. 

(At first I tried the line * sudo echo 0 > /proc/sys/net/ipv4/tcp_window_scaling* in terminal, but the reply was "permission denied" even without asking for my root pass.)

Just for refecence Bogart's post said:

> 
You might also want to try, as root:

echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

If it makes a difference, to make the change automatically at boot you can add a line to /etc/sysctl.conf with the following:

net.ipv4.tcp_window_scaling = 0

And if it doesn't make any difference, just revert the change with "echo 1 > /proc/sys/net/ipv4/tcp_window_scaling" (or reboot the computer, if you prefer).

---

### Post by Gen2ly on 2009-06-27
You might want to read this post about using sudo and echo:

[http://ubuntuforums.org/showthread.php?t=412329](http://ubuntuforums.org/showthread.php?t=412329)

Bacially this doesn't work because you're using shell-redirection to write a file as regular user.  Look at the post above to find out how to use "sudo echo" with Ubuntu.

---

### Post by External on 2009-06-29
Well I did learn some new stuff about sudo and echo, but as I wrote in my previous post, the suggestion unfortunately didn't solve the problem. Maybe something else could be the cause?

---

### Post by Gen2ly on 2009-07-01
...thinks alot...

Sure yeah... Have you tried disabling ipv6?

---

### Post by External on 2009-07-06
Yes, sorry for the delay in replying; disabling ipv6 in Firefox was one of the 1st things I tried with no success.

I also tried this suggestion to no avail:

```

echo "4096 16384 131072" > /proc/sys/net/ipv4/tcp_wmem
echo "4096 87380 174760" > /proc/sys/net/ipv4/tcp_rmem
```

Anyone any ideas, please...?

---

