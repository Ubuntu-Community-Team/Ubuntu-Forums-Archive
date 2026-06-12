---
title: "Network Manager will not auto-connect to new network after resume"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by Darwin Award Winner on 2010-07-01
[SIZE="3"]**The Problem**[/SIZE]

Hi all,

I recently fixed an annoying problem and I thought it would be nice to share my solution here. The problem was that after a cycle of suspend/resume, Network Manager would only auto-connect to the same network as it was previously connected to. So, for example, if I suspended my laptop at home, and then I went to school and resumed it, it would try to connect to the home network, and then just give up. It would not connect to the school network unless I explicitly told it to. 

[SIZE="3"]**The Solution**[/SIZE]

First, I'll describe the fix. If you're having this problem, you can this. Copy the following:

```
#!/bin/sh
case "$1" in
        resume|thaw)
                pkill NetworkManager
                ;;
        suspend|hibernate)
                # Do nothing
                ;;
esac
```

Create the file /etc/pm/sleep.d/10_restart-networkmanager and paste the above code into it. Make sure it is owned by root (the administrator) and is marked as executable. That's all. Now, try suspending your computer and then taking it away from your current wireless network to another one that it should auto-connect to. See if it works.

If this doesn't work for you and you want to undo the changes you have made, simply delete the file /etc/pm/sleep.d/10_restart-networkmanager.

[SIZE="3"]**How the solution works**[/SIZE]

Any executable script in the directory /etc/pm/sleep.d/ will be run on both suspend and resume. The script is told which action is currently happening. This particular script will only do something when the computer is resuming. When the computer resumes, it will run this script, which will kill Network Manager, causing it to forget what network it was previously connected to. However, it doesn't stay dead. Some part of the operating system is monitoring Network Manager and will respawn it after it is killed. It will then connect to the most appropriate network, free of any previous bias. 

[SIZE="3"]**Why the problem exists in the first place**[/SIZE]

In my case, I happen to know that the reason for my problem has to do with a problem in the Broadcom wireless drivers. The drivers don't support suspend in quite the correct way, so Network Manager thinks that it has last its connection unexpectedly, so it tries to reconnect.

Hope this helps people.


Edit: For Lucid, the following should work:

```
#!/bin/sh
case "$1" in
        resume|thaw)
                service network-manager restart
                ;;
        suspend|hibernate)
                # Do nothing
                ;;
esac
```

---

### Post by HaightsW on 2010-07-04
Cheers for sharing this DAW, it fixed my problem too!:)

---

### Post by wenfuli on 2010-07-06
DAW:

I am happy to say that your code partly worked, but frustrated to say that it didn't do what I was hoping.

The details of my problem are such:

I decided to try out the hibernate option. My machine hibernated fine, but did not want to wake back up. The only option left to me that I could think of was a manual restart. After the manual restart, my machine will not connect to either a wired or wireless connection (I was connected to a wired network at the time of initial hibernation). Right now in my network connection icon in the panel I get a red exclamation mark and the message "Networking disabled" when I move my mouse pointer over it.

The good news is that with your code, my machine now wakes up from both sleep and hibernate, which it did not do before. But, it did not solve my connection problem. My thought would be that some other code need to be put into that file, but I have no idea what. Can you -- or anyone else -- help?

Thanks,
Chuck

---

### Post by wenfuli on 2010-07-07
Please disregard my previous post(s). I figured out and solved the problem.

But I would like to thank DAW again -- at the very least suspend and hibernate now work on my machine. That wasn't the solution I was looking for originally, but I'm happy to have it regardless.

---

### Post by Darwin Award Winner on 2010-07-07
I don't think that anything I've described here could possibly fix suspend or hibernate. The script as I have written it doesn't even do anything at all until after the computer has already suspended and fully resumed.

---

### Post by deckoff on 2011-05-28
How exactly do I set the script to be owned by root? chmod 755?
Where should I put  the script - can it be

---

