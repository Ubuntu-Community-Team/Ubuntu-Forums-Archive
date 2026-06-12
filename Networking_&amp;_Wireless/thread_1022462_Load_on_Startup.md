---
title: "Load on Startup"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by efledderman on 2008-12-26
Ok, so I have a hell of a time getting my wireless working, but I finally did.  I fixed it with this code:

```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2008-10-31
make
sudo make install
sudo make unload
sudo make load
```The only issue that I have not, is that I have to rerun this part of the code every time Ubuntu starts up:

```

 cd compat-wireless-2008-10-31
 make
 sudo make install
 sudo make unload
 sudo make load
```Is there someway to get this code to stick so it doesn't need to be re-ran?

---

### Post by thomas228 on 2008-12-26
> **efledderman said:**
> Ok, so I have a hell of a time getting my wireless working, but I finally did.  I fixed it with this code:

```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2008-10-31
make
sudo make install
sudo make unload
sudo make load
```The only issue that I have not, is that I have to rerun this part of the code every time Ubuntu starts up:

```

 cd compat-wireless-2008-10-31
 make
 sudo make install
 sudo make unload
 sudo make load
```Is there someway to get this code to stick so it doesn't need to be re-ran?

Hi 

I'm not sure I can help you very easily as it has been awhile since I installed my AR5007 Atheros madwifi Hardy 

I was lucky enough to print post#1 of [http://ubuntuforums.org/showthread.php?t=795984]("http://ubuntuforums.org/showthread.php?t=795984")
and download the madwifi aircracked tar package

If you installed the 32bit Ubuntu Hardy OS I may be able to help you but it is quite involved so let me know if you want a little more help and I'll see what I can do.

Let me know

Tom

---

### Post by efledderman on 2008-12-26
Well, I'm for sure would love the help, but to clear things up... I actually have 32bit Intrepid.

---

### Post by kevdog on 2008-12-26
You could stick those commands on the /etc/rc.local file -- commands in this file are run at startup (you dont need the sudo prefix).  Place the commands prior to the exit at the bottom of the file.

---

### Post by ubuntubrian on 2009-01-18
I have the exact same issue. Is there no "official" solution?

---

