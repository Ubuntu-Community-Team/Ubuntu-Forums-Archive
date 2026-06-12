---
title: "WEP doesn't work, what does?"
date: 2006-03-24
forum: Networking &amp; Wireless
---

### Post by anagnost68 on 2006-03-24
!Newbie Warning!

I installed 5.1 (breezy?) yesterday and have a netgear WG311T card and a Linksys WRT54GL router.  It works fine until I try to use WEP.  

What I did:

I generate 4 keys from Linksys using a passphrase.  The Default Transmit Key is set to 1.  Then, on Ubuntu Network Admin, I type in the same WEP value as listed from Linksys.  I tried each of the four values that Linksys shows.  Nothing works.  I haven't tried any of the other settings on Linksys because the Network Admin dialog only allows the WEP key to be entered (how can you get WPA in there if there's no field for it?!).

What's the next step I can take to resolve this problem?

Thanks!

---

### Post by Jason_25 on 2006-03-24
The network admin on breezy is troublesome.  You'll quickly find that in order to get much done you will need to use the terminal.

Try
```

sudo iwconfig ath0 key insertkeyhere

```
and
```

sudo iwconfig

```
Will show wireless stats and list your key.

---

### Post by anagnost68 on 2006-03-24
thanks! worked like a charm!

---

### Post by anagnost68 on 2006-03-24
Can I do something similar for the other types of security such as WPA?  If so, what would the command line syntax be?

Thanks

---

### Post by Jason_25 on 2006-03-25
[This]("http://ubuntuforums.org/showthread.php?t=90450") thread has worked for me.  It works on dapper too, if that's what your using.

---

### Post by anagnost68 on 2006-03-26
What's dapper?

---

### Post by jml on 2006-03-26
Dapper is short for Dapper Drake.  Its the unofficial name to the version of Ubuntu currently under development.  It was originally scheduled for release in June of 2006, but for various reasons, its release has been pushed back about 6 weeks.  While its still in testing, a lot of brave souls :)  download and run testing on their computers.  The advantage is that you get access to the latest and greatest of Ubuntu's applications.  The disagvantage is that it is still in testing, while quite stable, things still do break.  So if you are relatively new to linux you are better off using the current release.

Joe

---

