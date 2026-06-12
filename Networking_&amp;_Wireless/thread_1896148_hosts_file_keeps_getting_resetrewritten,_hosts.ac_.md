---
title: "hosts file keeps getting reset/rewritten, hosts.ac the culprit"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by PhartSmellah on 2011-12-16
This post is to help others who've encountered the same problem. I've been looking (Google'ing) around for quite some time and have just now come up with the solution. Tried to make the title Google-friendly :)

Ever since a week ago, I haven't been able to change anything in the file. Whenever I reboot my system, the file gets overwritten.
Just to be clear - the file is not wiped and restored to an original (clean) state, it's instead reverted to a previous state. Older hosts I've added to the file are still there, but I just can't add any new hosts to the file. :confused:
Also, if I "sudo gedit /etc/hosts", the changes are saved for that session. But once I reboot, they're gone.

Looking into the /etc folder, I've found a file called **hosts.ac**, which seemed like a copy of my hosts file. When I tried changing it - Presto! The /etc/hosts file was changed to reflect the content of this file.

After some investigation, seems this file was added after installing Cisco AnyConnect (hence the ".ac"), and on every reboot, it copies this file over /etc/hosts.

So if you have AnyConnect - in order to make changes to hosts, _you need to edit /etc/hosts.ac_, not the original /etc/hosts file!

Hope this helps someone - was a big mystery for me...

---

### Post by stuwat on 2011-12-17
That problem has plagued me for far too long. I eventually took the time to do some investigating and found the hosts.ac file, which looked just like the version of the hosts file that I kept reverting back to, either on reboot or after connecting/disconnecting with Any Connect. I searched for hosts.ac on these forums and came across this post, which is the only mention of the problem I have seen anywhere. Thanks for sharing. Hopefully this will help others with the same problem.

---

### Post by turnersd on 2011-12-23
> **PhartSmellah said:**
> This post is to help others who've encountered the same problem. I've been looking (Google'ing) around for quite some time and have just now come up with the solution. Tried to make the title Google-friendly :)

Ever since a week ago, I haven't been able to change anything in the file. Whenever I reboot my system, the file gets overwritten.
Just to be clear - the file is not wiped and restored to an original (clean) state, it's instead reverted to a previous state. Older hosts I've added to the file are still there, but I just can't add any new hosts to the file. :confused:
Also, if I "sudo gedit /etc/hosts", the changes are saved for that session. But once I reboot, they're gone.

Looking into the /etc folder, I've found a file called **hosts.ac**, which seemed like a copy of my hosts file. When I tried changing it - Presto! The /etc/hosts file was changed to reflect the content of this file.

After some investigation, seems this file was added after installing Cisco AnyConnect (hence the ".ac"), and on every reboot, it copies this file over /etc/hosts.

So if you have AnyConnect - in order to make changes to hosts, _you need to edit /etc/hosts.ac_, not the original /etc/hosts file!

Hope this helps someone - was a big mystery for me...

Absolutely brilliant. You, sir, win the internet for the day. This same problem was bugging me to no end.

---

### Post by ANewBite on 2011-12-23
I've been an Ubuntu forums lurker for a while now. 

I went through the effort to register so I could give major kudos to the OP.  I had the exact same problem, and this fixed it!

I would add that /etc/hosts gets reset *every* time you connect with AnyConnect, as I observed it reverting even when I wasn't rebooting the machine.  Why AC generates another hosts file is either beyond my comprehension or really stupid.

---

### Post by mlevin2 on 2012-03-29
Thank you! That was driving me crazy!

I wrote a little script called "vihosts" (to be consistent with "vipw" and "vigr") -- now I just have to remember to type "vihosts" instead of "sudo vi /etc/hosts" and everything should be fine.

```
#!/usr/bin/env bash
FILE=`mktemp`
cp /etc/hosts $FILE && vi $FILE && sudo cp $FILE /etc/hosts && sudo cp $FILE /etc/hosts.ac && rm $FILE
```

---

### Post by bluefly on 2012-05-10
This has been driving me crazy, too.  Thanks so much for posting.

---

### Post by |{urse on 2012-05-10
:guitar:

---

### Post by brianhogg on 2012-07-07
Had the exact same problem on Mac OSX with Cisco AnyConnect, and was driving me insane.  Thanks for posting!

---

### Post by ruicovelo on 2012-08-07
Thanks for posting this!! I was about to throw my laptop out the window...

---

### Post by yangqio2 on 2012-08-12
yes,we can also make a soft link from hosts to hosts.ac
like this ```

&#21024;&#38500;&#21407;&#26469;hosts.ac
	sudo rm /etc/hosts.ac
	&#24314;&#31435;&#36719;&#38142;
	sudo ln -s /etc/hosts.ac /etc/hosts
```

visit [http://llohellohe.github.com/mac/mac-linux-hosts-reset-rewritten.html](http://llohellohe.github.com/mac/mac-linux-hosts-reset-rewritten.html) for more details

---

### Post by edburns on 2012-08-17
Thank you very much.  I also ran into this problem on Mac Os X.  Your post was very helpful.

Sincerely,

Ed Burns

---

### Post by gctaylor1 on 2012-08-30
Just another grateful user thanking you for posting this.

---

### Post by sopvkore on 2012-11-06
The problem seems to be resolved with the recent version of Cisco AnyConnect (3.1.01065). Can anyone confirm?

---

### Post by stuttle on 2013-04-10
Thank you, thank you, thank you!
This has plagued me for quite some time. Your post is [U]still[I] helping people!!

[/I][/U]

---

### Post by rodolfo.baselli on 2013-11-12
The VPN client suddenly earned itself a nice
```
update-rc.d -f vpnagentd_init remove
```
just as any other intrusive piece of software.

Thanks :-)

---

### Post by gabbon on 2014-06-05
This was anoying me as well.
I deleted my hosts file and made a symbolic link to the hosts.ac not sure what will happen when I reboot.

---

