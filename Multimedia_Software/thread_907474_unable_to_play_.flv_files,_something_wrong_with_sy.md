---
title: "unable to play .flv files, something wrong with synaptic"
date: 2008-09-01
forum: Multimedia Software
---

### Post by scrumpypaul on 2008-09-01
hello everyone,

i'm an ubuntu virgin, so-to-speak.

can anyone providing help, please, please, give it in laymans terms.

i tried to go via applications-install new application, but got this message.........

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

'/etc/apt/sources.list' means nothing to me, at all, and trying both sudo thingys in the "run application" box doesn't seem to do anything.

can anyone help me?

i've tried and failed to install vlc.


thanks in advance.





by the way, when i checked the sources.list file and tried to update it, i got the following message


E: Malformed 3rd word in the Status line
E: Error occurred while processing ttf-bitstream-vera (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.




hope this helps you to help me.......................

---

### Post by ad_267 on 2008-09-01
Can you go to applications - accessories - terminal and enter those commands:

```

sudo apt-get update
sudo apt-get install -f

```

Then post back the output if that doesn't fix things.

You should also be able to play flv with totem if you install ubuntu-restricted-extras.

---

### Post by scrumpypaul on 2008-09-01
hi

this was the result

E: Malformed 3rd word in the Status line
E: Error occurred while processing ttf-bitstream-vera (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
paul@pauls-laptop:~$ 






E: Malformed 3rd word in the Status line
E: Error occurred while processing ttf-bitstream-vera (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
paul@pauls-laptop:~$ 






how would i install the totem extras?

---

### Post by ad_267 on 2008-09-01
Once you have this fixed you can install that through synaptic or add/remove.

You could try clearing the list of packages with:
```

sudo dpkg --clear-avail 
sudo apt-get update

```

If that doesn't work you could try reverting the status file to an old version if there is one.
First make sure there is a file called status-old:
```

ls /var/lib/dpkg/status*

```
Then use:
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status_backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status

```

Oh and another thing that could help is in synaptic package manager go to Edit - Fix Broken Packages.

---

### Post by scrumpypaul on 2008-09-01
ad-267 - i have no idea what you have told me to do or whether i actually followed your instructions correctly, but voila, hey presto, quelle fromage - it's worked.


you are a star - cheers very much.:)

---

### Post by ad_267 on 2008-09-01
Awesome. I don't know why that happened but I'm glad it's fixed now.

---

