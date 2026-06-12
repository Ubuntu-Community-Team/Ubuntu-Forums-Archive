---
title: "VLC not playing"
date: 2018-04-20
forum: Multimedia Software
---

### Post by Rixter69 on 2018-04-20
Installed VLC per these instructions  [[https://tecadmin.net/install-vlc-on-ubuntu/]](https://tecadmin.net/install-vlc-on-ubuntu/]) It would not play/open. Installed all codes pkg, restricted extras. Purged VLC via terminal and went to software centre. There VLC did not have an install icon. VERY strange! OK, anyone want to take a stab at this? Just want to be able to use VLC...as I have in the past.   Ubuntu 17.10 xfce

[SIZE=3][FONT=times new roman]***Rick***[/FONT][/SIZE]

---

### Post by &amp;KyT$0P# on 2018-04-20
> **Rixter69 said:**
> Just want to be able to use VLC..
Then why not just use the VLC available in the standard Ubuntu repositories?  Is there a specific reason you want to use a pre-release version of VLC?

---

### Post by Rixter69 on 2018-04-25
RE:  [I][B]Everyone

   [/B][/I]I'd had enough and just wasn't getting anywhere, so, wiped distro and installed another. At this point....all seems to be working. Let's hope it stays that way. Appreciate all who responded. I don't think if would be fair to mark this thread solved, for I really didn't *solve* anything, but then, it's true that I shouldn't leave it open. What is best idea to resolving this thread's fate?

[I][B]THX:
[/B][/I]
[SIZE=4][FONT=times new roman]***Rick***[/FONT][/SIZE]

---

### Post by monkeybrain20122 on 2018-04-26
vlc installed in software centre is a snap package. It is kind of experimental

```
sudo apt install vlc
```

will install the deb package and that should work.

To avoid installing snap packages accidentally use synaptic instead of software center
```

sudo apt install synaptic
```

It doesn't have the pretty picture but a much better and feature complete GUI package manager than software center, and no snap package in there.

I think they should only offer snap packages in software center when no .deb is available, enthusiasts can easily install snap packages from command line if they choose to, but pushing half baked snap packages in software center just ruins Ubuntu's reputation for new users.

---

### Post by Rixter69 on 2018-04-26
RE: [I]**monkeybrain**

**   Thanx for responding. OK, some good. useful info there. I was wondering about "snap" as well. As with every "jonny-come-lately" package, I always wait for a bit and give it time to work the bugs out, then decide if it's a package I should have. VLC has/had worked fine for me and I didn't see cause to run inside/with snap. But, I digress...the problems I experienced were due to running "live" and not employing one very critical command...**[COLOR=#0000FF]**apt-cdrom. **[/COLOR][B]Did not know about it and "accidentally" stumbled across it when running updates. Wish there was a way to 'publish" this command and why to use it when running a distro live. Anyway, kudos for the info you passed.

[COLOR=#0000ff][/COLOR][FONT=times new roman][SIZE=4]Rick[/SIZE][/FONT][/B][/I]

---

