---
title: "Installing Cisco Packet Tracer 5.3.3"
date: 2013-04-22
forum: Networking &amp; Wireless
---

### Post by blanka32 on 2013-04-22
So I followed the guide from [here]("http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file") on how to install with CLI, but I get to the step ```
xdg-open INSTALL
``` 
and it just opens the file as a text file. I then do ```

./configure 
make
sudo make install
```

and gives me back

```
./configure
bash: ./configure: No such file or directory
make
make: *** No targets specified and no makefile found.  Stop.
sudo make install
make: Nothing to be done for `install'.


```

I've done this before so I may be missin something here, anyone have any clue what I could be doing wrong?

---

### Post by blanka32 on 2013-04-23
bump

---

### Post by bab1 on 2013-04-23
Those are 3 different commands.

1```
./configure
```

2```
 make
```

3```
 sudo make install
```

---

### Post by blanka32 on 2013-04-23
> **bab1 said:**
> Those are 3 different commands.

1```
./configure
```

2```
 make
```

3```
 sudo make install
```

I understand, I clumped the results in the same code box to cut for space.

---

### Post by blanka32 on 2013-04-24
Alright, I found a solution. I have a 64 bit processor and packet tracer was designed for 32 bit. If anyone else is in a similar situation, go to [this website]("http://kaslnetwork.com/articles/installing-cisco-packettracer-5-3-2-on-64-bit-ubuntu-or-debian/") and follow their instructions.

---

