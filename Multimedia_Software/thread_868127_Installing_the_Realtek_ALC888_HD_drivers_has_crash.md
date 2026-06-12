---
title: "Installing the Realtek ALC888 HD drivers has crashed system. Help"
date: 2008-07-23
forum: Multimedia Software
---

### Post by ewh1533 on 2008-07-23
Well, considering I was having a few problems with the native audio driver, I decided to look into getting the actual drivers from realtek.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs")

I unzipped the file, then ran sudo ./install in the directory.

A huge amount of errors start up during the install. I restart, and now the system will not run. It gets to the login, and shuts down afterward saying my session only lasted 10 seconds and gives me an error message. 

```

/ect/gdm/xsession: beginning session setup
Setting IM through im-switch for local=En Us
start IM through /ect/x11/xinit/xinput.d/all_ALL linked to /ect/xinit/xinput.d/default
/usr/bin/seahorse-agent: error while loading shared libraries: Libasound.so.2: cannot open shared object file: No such file or directory.

```
How do I get my system back the way it was.. I can only run safemode terminal, anything else shuts down the GUI and gives me that error?

---

### Post by ewh1533 on 2008-07-23
Ok, I resolved that issue by doing the following:

started up a safe session with termimal

sudo apt-get install build-essentials

then reinstalled the drivers. I get an error at the end of the installation, and no sound works, but at least I'm able to start up my puter.

---

### Post by ewh1533 on 2008-07-23
./install: 101: alsaconf: not found


Ok, I don't know exactly what it's asking for here, but thats the error at the end of the file. I'm assuming it need some sort of config parameters to hash out the last bits of the install. Any help?

---

### Post by MTHusker on 2008-08-02
I'm having the exact same problem.  I followed your instructions, running sudo apt-get install build-essentials, but at the end there's and error that states build-essentials could not be found.  I went ahead and reinstalled the drivers, but I still cannot log in.  This is my very first linux install, so I'm not familiar with command-line troubleshooting steps.  Any suggestions would be greatly appreciated.

---

### Post by daveisfera on 2009-03-20
I was able to get this working with mythbuntu 8.10 by adding ncurses and xmlto. The exact command I used was:

```
sudo apt-get install build-essential linux-headers-generic libncurses5-dev xmlto

```

---

