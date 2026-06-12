---
title: "Trouble installing LIRC 0.8.7 CVS"
date: 2010-06-26
forum: Mythbuntu
---

### Post by Kdar on 2010-06-26
I am using Ubuntu 9.10, but hopefully this problem with common with Mythbuntu.

I was trying to install latest version of LIRC using instructions on this page:
[http://www.lirc.org/cvs.html](http://www.lirc.org/cvs.html)
```

cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
cd lirc
./autogen.sh
./setup.sh
sudo make
sudo make install
```

After this, I typed "sudo checkinstall" in the same directory to create .deb file. Next I install that .deb file

However, I don't think it fully installed LIRC. Since typing "lirc -v" doesn't have any output (it tells there is no such file). If I go to /etc/lirc there is only lircd.conf
If I go to /dev/, lircd or lirc0 doesn't exist. Also there is not lirc in /etc/init.d/ directory (thats probably why lirc -v doesn't work). So it basically, lirc would not start and irw doesn't work to test remote.
In side of /etc/init.d, there are only files: lircd, lircmd and lircrcd (I am not sure what they do).

One strange thing is that, with CVS version, my USB receiver for remote seem to act better.. when I press something on remote, the light on the received flash only when it is pressed, and off when it is released.
With version from synaptic, that light on received always stays on.

---

### Post by klc5555 on 2010-06-26
> **Kdar said:**
> I am using Ubuntu 9.10, but hopefully this problem with common with Mythbuntu.

I was trying to install latest version of LIRC using instructions on this page:
[http://www.lirc.org/cvs.html](http://www.lirc.org/cvs.html)
```

cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
cd lirc
./autogen.sh
./setup.sh
sudo make
sudo make install
```

After this, I typed "sudo checkinstall" in the same directory to create .deb file. Next I install that .deb file

However, I don't think it fully installed LIRC. Since typing "lirc -v" doesn't have any output (it tells there is no such file). If I go to /etc/lirc there is only lircd.conf
If I go to /dev/, lircd or lirc0 doesn't exist. Also there is not lirc in /etc/init.d/ directory (thats probably why lirc -v doesn't work). So it basically, lirc would not start and irw doesn't work to test remote.
In side of /etc/init.d, there are only files: lircd, lircmd and lircrcd (I am not sure what they do).

One strange thing is that, with CVS version, my USB received for remote seem to act better.. when I press something on remote, the light on the received flash only when it is pressed, and off when it is released.
With version from synaptic, that light on received always stays on.

The command should be "lircd -v", not "lirc -v" It will probably should the old version of lircd is running.

I had a similar problem upgrading lirc in Mythbuntu 9.04 from 0.8.4a to 0.8.6. I couldn't use the version of 0.8.6 from Canonical, because oddly they don't include the iguanaIR driver in it, so I compiled from source from lirc.org

A standard "make/make install" of source from lirc.org appears to put files where Ubuntu does not expect to find them. You may find that you ended up with a lircd in both /usr/sbin/ and /usr/local/sbin/  The newer one likely ended up in /usr/local/sbin/, while Ubuntu is running the older one at /usr/sbin/ Other files may similarly have multiple versions. hardware.conf may have ended up under /etc rather than /etc/lirc

---

### Post by Kdar on 2010-06-26
thank for your reply.
I got it working on my laptop (which I used for testing purposes, so I can follow same procedure on my HTPC, to get this receiver working).
I removed previously install LIRC by make uninstall and removing from apt-get. Next I install CVS version by make & make install, and than reinstalled version from apt-get "sudo apt-get install lirc". This somehow worked (maybe CVS version had some extra files which wasn't included in Ubuntu's repository).

On Laptop it works just fine, I even installed XBMC to see if it will work there, and it did.

However, when I started to do the same things on my HTPC (the installation of LIRC). I did everything 100% same like what I did on laptop. Next, on HTPC, I connected receiver into USB port and run irw in terminal. I tried pressing few things on my remote...irw didn't return anything.. and also receiver's light after that would not turn off.

In contrast, on Laptop that light would show up only when something pressed.

What do you think is wrong with it?

---

### Post by klc5555 on 2010-06-26
I'm surprised that completely uninstalling lirc with apt-get didn't rip out all of the guts of mythtv, for which lirc is a dependency. The deb package manager can be really annoying that way. Anyhow, was "./configure" run (from the downloaded code's "makefile" directory) prior to the compile to provide the right driver for your receiver? If this thing had been installed from a .deb, you'd use "sudo dpkg-reconfigure lirc". With locally compiled source however you have to run ./configure again and then recompile.

If configured and compiled correctly, is lircd actually running? If "make install" put the files (particularly lircd) in the wrong (for Ubuntu) places (which I suspect), the daemon won't start automatically. See if you can start it from a terminal "sudo lircd -n" If lircd is started and running from a terminal, then you can play with irw again, and perhaps get more information (in the terminal) if it doesn't function. 

If everything appears to be configured, compiled, "make-installed", started, and running correctly, but nothing works and you're still getting no info to debug from, then you may have to recompile lirc in debug mode, as the docs at lirc.org suggest.

---

### Post by DiabboVerdde on 2010-08-26
I am having a different problem, but it is related with this topic. I download CVS code, compile it, install, create the lirc file for /etc/init.d, and both lircd and lircmd daemons come up as expected. However I get no "lirc" device of any kind on /dev, such as /dev/lirc.

I can run irrecord to create the lircd.conf file, run irw to test it, and it works. But mythbuntu or even my instance of XBMC can't use the control because there's no device...

Does anybody has any thoughts or ideas on how to fix this?

Regards,

DiabboVerdde

---

