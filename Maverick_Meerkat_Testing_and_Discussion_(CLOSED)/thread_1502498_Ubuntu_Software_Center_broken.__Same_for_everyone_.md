---
title: "Ubuntu Software Center broken.  Same for everyone else?"
date: 2010-06-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by crjackson on 2010-06-05
While testing, I noticed that the software center doesn't load anymore.  Does everyone else have this particular breakage?

---

### Post by paul_in_london on 2010-06-05
I don't use it myself, but just checked and it loads ok for me...

---

### Post by ranch hand on 2010-06-05
Sounds like a great feature to me.  Can't stand USC.

---

### Post by crjackson on 2010-06-05
> **ranch hand said:**
> Sounds like a great feature to me.  Can't stand USC.

Ha ha ha... Can't say I disagree.  It may have been broken all along, I just thought I would check it out today and found it wouldn't load.

So it seems that it's unique to my system then.

---

### Post by ranch hand on 2010-06-05
OK, OK, so I reedited my menu so it shows up and loaded it just fine.

Reedited menu so it does not show up.

Hey, I am a good boy, I haven't uninstalled it.  I think that shows great restraint.

---

### Post by crjackson on 2010-06-05
> **ranch hand said:**
> OK, OK, so I reedited my menu so it shows up and loaded it just fine.

Reedited menu so it does not show up.

Hey, I am a good boy, I haven't uninstalled it.  I think that shows great restraint.

Hey Ranch, we're supposed to be testing EVERYTHING aren't we?

Here's what I get from a terminal;

```
charles@emachines-laptop:~$ software-center
/usr/share/software-center/softwarecenter/view/historypane.py:29: DeprecationWarning: please use 'debian' instead of 'debian_bundle'
  from debian_bundle import deb822
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 206, in __init__
    self.icons, datadir)
  File "/usr/share/software-center/softwarecenter/view/historypane.py", line 128, in __init__
    self.parse_history_log()
  File "/usr/share/software-center/softwarecenter/view/historypane.py", line 163, in parse_history_log
    when = datetime.datetime.strptime(stanza['Start-Date'], '%Y-%m-%d %H:%M:%S')
  File "/usr/lib/pymodules/python2.6/debian/deb822.py", line 170, in __getitem__
    value = self.__dict[key]
KeyError: 'Start-Date'
charles@emachines-laptop:~$
```

---

### Post by Starks on 2010-06-05
I've only used the USC once or twice.

Worthless for veteran Ubuntu users.

---

### Post by seeker5528 on 2010-06-05
> **crjackson said:**
> 
```
    value = self.__dict[key]
KeyError: 'Start-Date'
charles@emachines-laptop:~$
```

Is your date and time set correctly?

Later, Seeker

---

### Post by zekopeko on 2010-06-05
> **Starks said:**
> I've only used the USC once or twice.

Worthless for veteran Ubuntu users.

Probably because you aren't the targeted group as of yet.

---

### Post by crjackson on 2010-06-05
> **seeker5528 said:**
> Is your date and time set correctly?

Later, Seeker

Yes I saw that strange error.  It's set correctly.

---

### Post by crjackson on 2010-06-05
> **Starks said:**
> I've only used the USC once or twice.

Worthless for veteran Ubuntu users.

Not really true.  I've recently setup Lucid for a couple of new users.  Neither of them could grasp the concept of the package manager (as simple as it is), but the software center was quickly embraced and loved.  It was very useful for me because I didn't have to spend hours directing them on how to find the software of their choice and I didn't have to tell them how to install.

I found it very helpful since I got to go home early.

---

### Post by cariboo on 2010-06-05
I also don't use the Software Center, but because of this thread i tried it, and get the same error as the op. So if you want to file a bug, I can confirm it.

---

### Post by ronacc on 2010-06-05
I don't use USC regularly but check it from time to time in the spirit of testing . It is working ok on my system , AMD64 , updated a few minutes ago .

---

### Post by ronacc on 2010-06-05
I do havve one question about USC . Why is google earth not in there ? there are many google apps that are there ,g-talk ,g-gadgets etc,etc but no g-earth a VERY popular and useful app , thank the deities for Medibuntu .

---

### Post by Rasa1111 on 2010-06-05
USC is working fine here also. 
hmm..

---

### Post by noelvh on 2010-06-05
I gave the Software center a go and well will never use it. I install a number of items with it and none of the software ran after installed. I messed around and found it did not install files that are needed but are not part of the software. So for me this is a half *** installer (I mean no offense) I know it must have taken very long and loads of hard work to get it here, but a new user would give up on the first failure.

The best way is synaptic package manager, apt-get, or direct deb files.

Noel 

PS same goes for Linux Mints software center.

---

### Post by seeker5528 on 2010-06-05
If they were needed but not part of the software, they would be dependencies.

If these other packages were not needed, but have some moderately high importance level relative to features people expect to work in the software being installed then it most commonly would be recommended and by default recommends are treated as dependencies.

If these additional "needed but are not part of the software" packages were not installed when you installed the software using Software Center, then they shouldn't get install when you install the same software with Synaptic.

Later, Seeker

---

### Post by go7Ul1ai on 2010-06-05
Works fine here

---

### Post by ranch hand on 2010-06-05
> **noelvh said:**
> I gave the Software center a go and well will never use it. I install a number of items with it and none of the software ran after installed. I messed around and found it did not install files that are needed but are not part of the software. So for me this is a half *** installer (I mean no offense) I know it must have taken very long and loads of hard work to get it here, but a new user would give up on the first failure.

The best way is synaptic package manager, apt-get, or direct deb files.

Noel 

PS same goes for Linux Mints software center.
I may not like the USC but I certainly hope you filed a bug;
```

ubuntu-bug software-center

```
filing bugs is what we are here for.  That  is our function in this process of building this release.

---

### Post by crjackson on 2010-06-05
> **cariboo907 said:**
> I also don't use the Software Center, but because of this thread i tried it, and get the same error as the op. So if you want to file a bug, I can confirm it.

Okay, I'll work on the bug report tomorrow.  I'm on a Lucid machine right now.

---

### Post by Mr. Picklesworth on 2010-06-05
> **noelvh said:**
> I gave the Software center a go and well will never use it. I install a number of items with it and none of the software ran after installed. I messed around and found it did not install files that are needed but are not part of the software. So for me this is a half *** installer (I mean no offense) I know it must have taken very long and loads of hard work to get it here, but a new user would give up on the first failure.

The best way is synaptic package manager, apt-get, or direct deb files.

Noel 

PS same goes for Linux Mints software center.

Err, just to clear things up, Software Centre calls aptdaemon, which uses libapt; the same thing Synaptic and apt-get use. If something doesn't install properly, it is hardly Software Centre's fault.
(Although it could communicate a bit better with regards to dependencies, suggestions and errors. That will be happening, and will be happening quicker if everyone is nice to it. Right now, it's very shy because people are mean to it).

And to restore balance against the Software Centre bashing, I actively choose it over Synaptic for many tasks because it is a heck of a lot faster and it doesn't run as root. Searching is practically instant, I can easily find packages from specific repositories, it can do awesome things without worrying about security or integration, and there isn't a long delay when I open it up.
Oh, and it looks kinda pretty :)

---

### Post by SteamInc on 2010-06-06
I have the same problem, but im missing some files from the update that doesn't allow me to install anything im working on fixing it.

---

### Post by zekopeko on 2010-06-06
> **Mr. Picklesworth said:**
> And to restore balance against the Software Centre bashing, I actively choose it over Synaptic for many tasks because it is a heck of a lot faster, and doesn't run as root all the time. Searching is practically instant, I can easily find packages from specific repositories, and there isn't a long delay when I open it up.
Oh, and it looks kinda pretty :)

Agreed. I hope they manage to include the redesign of the sub-departments in USC3. I hate the dual pane/scrollbars approach.

---

### Post by null_pointer_us on 2010-06-06
USC is really bad when packaging is broken (e.g. during development cycle) because it does not warn when important things will be added/removed.

The major gripe I have with USC right now is that More Info always leads to a blank page.

---

### Post by mc4man on 2010-06-10
> While testing, I noticed that the software center doesn't load anymore.

The update today of sc should return use if it was failing to load, though it possibly could fail again till python-debian is patched
[https://launchpad.net/ubuntu/+source/software-center/2.1.2/+changelog](https://launchpad.net/ubuntu/+source/software-center/2.1.2/+changelog)

---

### Post by crjackson on 2010-06-10
> **mc4man said:**
> The update today of sc should return use if it was failing to load, though it possibly could fail again till python-debian is patched
[https://launchpad.net/ubuntu/+source/software-center/2.1.2/+changelog](https://launchpad.net/ubuntu/+source/software-center/2.1.2/+changelog)

Yup...  It's working again now.

---

