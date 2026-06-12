---
title: "Skype for my 15.10 Ubuntu?"
date: 2016-02-02
forum: Multimedia Software
---

### Post by helm10101 on 2016-02-02
Will Skype 4.3 work on my Ubuntu 15.10 if I download the Ubuntu 12.04 multiarch (the closest option at Skype website to my Ubuntu version)?
Thanks

---

### Post by Vladlenin5000 on 2016-02-02
Yes, but better to install it directly from the repos.
Open System settings > Software Properties and then the 'other software' tab. Tick the Canonical Partners repo and close the dialog. Then
```
sudo apt-get update
sudo apt-get install skype
```

---

### Post by helm10101 on 2016-02-03
> **Vladlenin5000 said:**
> Yes, but better to install it directly from the repos.
Open System settings > Software Properties and then the 'other software' tab. Tick the Canonical Partners repo and close the dialog. Then
```
sudo apt-get update
sudo apt-get install skype
```

when I do that, I get "Unable to locate package skype"

---

### Post by Vladlenin5000 on 2016-02-03
If so, you missed one of the steps. Read again carefully and double-check the partners repo.

---

### Post by inh38 on 2016-02-04
One workaround that I found, which might or might not work in your case, is to use [Skype online]("https://web.skype.com/en/"). I haven't tested their plugin for video conversation, but the chat works.

---

### Post by phinn2 on 2016-02-04
Have you tried downloading it directly from there website? I noticed its only for 12.04 but it may still be worth a shot.

---

### Post by ian-weisser on 2016-02-04
> **phinn2 said:**
> Have you tried downloading it directly from there website? I noticed its only for 12.04 but it may still be worth a shot.

Politely disagree.
Try Vladlenin5000's advice first.
Always try the tested and supported versions in the Ubuntu repositories first. Get into that habit.
Tested and compatible software in the Ubuntu repositories is one of the great strengths of Ubuntu. 

Downloading versions from the (dirty) internet for a different release of Ubuntu is not recommended for new users or unskilled users.
It might work, it might not.
Downloading random debs is not supportable in this forum - if you do it, and something breaks, our only useful advice will be 'uninstall the non-Ubuntu version, and install the supported Ubuntu version.'
And manually downloading debs is a hassle compared to the faster, simpler, supported way of installing great software onto your Ubuntu system.

---

### Post by helm10101 on 2016-02-05
You told me to get the supported versions first but, the fact is that I need to go to settings, and tick a "V" on "Canonical Partners", which was not marked by default. Why is that, if it's safe to do that in the first place?
Also, after I did that in this way, (ticking Canonical Partners repos), it told me that Skype needs additional 350 mb to install. Why does Skype need that much?
And now that I already installed it, how can I view what was installed when I wrote "sudo apt-get install skype", or how can I completely remove all those 350MB that were installed?
Isn't it too much, or suspicious? maybe I installed something bad except for skype? :o Sorry I'm so suspicious, I am just really new to Linux

---

### Post by Vladlenin5000 on 2016-02-05
Canonical Partners contain third-party closed source software, reason enough to not be active by default.
I don't know where the 350MB come from but my educated guess is "dependencies", the same that would have been pulled had you use the downloaded deb. Anyway, you were presented with a list of the exact packages that would be downloaded and installed before you agreed to install and everything is in the APT history so, no worries. 
And frankly, so much concern about "bad things" when you chose to install a closed source software from Microsoft? Really? It would be funny if it weren't so sadly revealing.

---

### Post by helm10101 on 2016-02-05
Thank you for your help Vladlenin5000

> **Vladlenin5000 said:**
> Canonical Partners contain third-party closed source software, reason enough to not be active by default.
I don't know where the 350MB come from but my educated guess is "dependencies", the same that would have been pulled had you use the downloaded deb. Anyway, you were presented with a list of the exact packages that would be downloaded and installed before you agreed to install and everything is in the APT history so, no worries. 
And frankly, so much concern about "bad things" when you chose to install a closed source software from Microsoft? Really? It would be funny if it weren't so sadly revealing.

You've got a point :D ,
And wow, so many dependencies. it's about 10 times the size of Skype., It sure relies on many dependencies!

---

### Post by ian-weisser on 2016-02-05
> **helm10101 said:**
> it's about 10 times the size of Skype., It sure relies on many dependencies!
That's how most big, complicated software works on most OSs.
In Windows and OSx (and Snappy), all those dependencies are still there, bundled with the application and hidden from view.

---

