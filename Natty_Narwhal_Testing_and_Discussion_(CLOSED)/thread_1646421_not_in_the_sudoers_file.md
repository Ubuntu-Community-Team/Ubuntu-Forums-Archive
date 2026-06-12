---
title: "not in the sudoers file"
date: 2010-12-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2010-12-15
I just ran updates and was prompted to update the sudoers file. It prompted me when it got to this and said something along the lines of, "If you're not sure what to do here, its recommended to click ok." So I did, and now I'm prompted with:

> kyleabaker is not in the sudoers file.  This incident will be reported.

I've done a quick search and found it reported, but the suggestions don't work since I'm unable to edit the list via "visudo". Any suggestions? Maybe I can edit this from the Live installation disc?

---

### Post by jmmL on 2010-12-15
Just done this myself. Kicked myself as soon as I agreed to the change.

My plan is to boot into recovery mode in grub, choose netroot and then add myself to the sudoers file.```

echo 'loginname ALL=(ALL) ALL' >> /etc/sudoers

``` where loginname is your user name.

Just seen the other thread: [http://ubuntuforums.org/showpost.php?p=10243477&postcount=2](http://ubuntuforums.org/showpost.php?p=10243477&postcount=2)
I will probably use that method instead.

---

### Post by kyleabaker on 2010-12-15
Thanks, dropping to netroot worked for me.

---

### Post by godhika on 2010-12-15
Ha! Had exactly the same problem (used the same fix) this evening. Guess there will come some more folks stumbling into this.

---

### Post by ratcheer on 2010-12-15
They got me too, guys. This was a pretty good trick.

Tim

---

### Post by ronacc on 2010-12-15
when an update wants to replace a config file atleast look at the differences if you are thinking about saying yes , I always "just say no" .

---

### Post by Quackers on 2010-12-15
> **ronacc said:**
> when an update wants to replace a config file atleast look at the differences if you are thinking about saying yes , I always "just say no" .

Lol, I stopped saying yes some time ago :-)

---

### Post by autocrosser on 2010-12-15
That's the first thing I did--looked at the diff & said "No thanks--I'll pass"  I left the config just the way I had edited it.

---

### Post by autocrosser on 2010-12-15
> **Quackers said:**
> Lol, I stopped saying yes some time ago :-)

Isn't just saying "Yes" a windozs crazie thing??????

---

### Post by Quackers on 2010-12-15
Having said that though, my timestamp amendments have stopped working, even though the file is as it was before.

---

### Post by autocrosser on 2010-12-15
What logs are you looking at?

---

### Post by Quackers on 2010-12-15
visudo

---

### Post by kyleabaker on 2010-12-15
I just got a second update for this file that was apparently released to avoid/fix this problem any further.

---

### Post by autocrosser on 2010-12-16
> **Quackers said:**
> visudo

Hmmm---all looking "normal" here--I'll keep an eye on things.....

---

