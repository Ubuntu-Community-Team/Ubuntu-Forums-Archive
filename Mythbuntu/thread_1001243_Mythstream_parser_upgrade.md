---
title: "Mythstream parser upgrade"
date: 2008-12-03
forum: Mythbuntu
---

### Post by elrodcarrera on 2008-12-03
I have Mythbuntu 8.10 installed and the shoutcast parser in mythstream needs to be updated. Is there a How To anywhere that a simpleton as myself can follow. I have tried following some of the posts dealing with this issue without any success. So... if someone could hold my hand and walk me through this it would be greatly appreciated.

---

### Post by tgm4883 on 2008-12-03
Can you try adding the mythbuntu-testing PPA and then installing mythstream-parser-shoutcast

You will need to add this line
```
deb http://ppa.launchpad.net/mythbuntu-testing/ubuntu intrepid main

```

to /etc/apt/sources.list

Then just 
```

sudo apt-get update
sudo apt-get install mythstream-parser-shoutcast
```

Hopefully that should work

---

### Post by elrodcarrera on 2008-12-03
> **tgm4883 said:**
> Can you try adding the mythbuntu-testing PPA and then installing mythstream-parser-shoutcast

You will need to add this line
```
deb http://ppa.launchpad.net/mythbuntu-testing/ubuntu intrepid main

```

to /etc/apt/sources.list

Then just 
```

sudo apt-get update
sudo apt-get install mythstream-parser-shoutcast
```

Hopefully that should work

Thanks for the suggestion
I tried this and I still get "No URL".
I checked the parser and it did upgrade but for some reason Shoutcast still does not load up. 
Is there anything else I can try?

---

### Post by bmwman on 2008-12-04
Try this [http://ubuntuforums.org/showthread.php?t=927300&page=3]("http://ubuntuforums.org/showthread.php?t=927300&page=3")

Post# 26

;)

---

