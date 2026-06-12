---
title: "mythbunto 7.10 install fails,help please!"
date: 2007-11-04
forum: Mythbuntu
---

### Post by gsrcrxsi on 2007-11-04
well i successfully installled Mythbuntu on my backend. setup as a backend/frontend for my bedroom. everything installed and setup fine.

but when i tried to install the frontend only on the frontend machine, the install fails at 83%. 

this is the traceback. i dont know what i means:

```
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 212, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 207, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 65, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 252, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 330, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/mythbuntu_install.py", line 288, in <module>
    install.run()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 100, in run
    self.configure_mythbuntu()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 179, in configure_mythbuntu
    raise InstallStepError("MythbuntuApply Debconf Xfer failed with code %d" % ret)
InstallStepError: MythbuntuApply Debconf Xfer failed with code 255 
```

backend specs:

asus p4g8x deluxe ATX MB
P4 2.4 GHz
1GB ram
500 GB HD
ATI 9600 

frontend:

Intel DG965PZ picoBTX MB
celeron 1.8GHz
1 GB ram
40 GB HD
Nvidia GeFroce 7300GT

can anyone help me resolve this? ive tried installing the frontend many times and it fails everytime the same way.

---

### Post by superm1 on 2007-11-04
> **gsrcrxsi said:**
> well i successfully installled Mythbuntu on my backend. setup as a backend/frontend for my bedroom. everything installed and setup fine.

but when i tried to install the frontend only on the frontend machine, the install fails at 83%. 

this is the traceback. i dont know what i means:

```
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 212, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 207, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 65, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 252, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 330, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/mythbuntu_install.py", line 288, in <module>
    install.run()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 100, in run
    self.configure_mythbuntu()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 179, in configure_mythbuntu
    raise InstallStepError("MythbuntuApply Debconf Xfer failed with code %d" % ret)
InstallStepError: MythbuntuApply Debconf Xfer failed with code 255 
```backend specs:

asus p4g8x deluxe ATX MB
P4 2.4 GHz
1GB ram
500 GB HD
ATI 9600 

frontend:

Intel DG965PZ picoBTX MB
celeron 1.8GHz
1 GB ram
40 GB HD
Nvidia GeFroce 7300GT

can anyone help me resolve this? ive tried installing the frontend many times and it fails everytime the same way.
Please post the /var/log/installer/syslog and specify what options you chose during install.  It's very possible that you found a bug.

---

### Post by gsrcrxsi on 2007-11-04
i dont know what that log is, since i have overwritten everything on another install. 

my options were :

advanced install -> frontend only. it doesnt seem to matter what options i chose after that, they all failed under the frontend only installation.

my fix was:

installed backend/frontend setup, then after the install i uninstalled everything pertaining to mythtv then reinstalled the Frontend metapackage via synaptic. everything works now. but i do have a desktop environment that i dont really need. how would i go about removing that, and having the computer load straight into mythtv with a splash screen?

---

### Post by superm1 on 2007-11-05
> **gsrcrxsi said:**
> i dont know what that log is, since i have overwritten everything on another install. 

my options were :

advanced install -> frontend only. it doesnt seem to matter what options i chose after that, they all failed under the frontend only installation.

my fix was:

installed backend/frontend setup, then after the install i uninstalled everything pertaining to mythtv then reinstalled the Frontend metapackage via synaptic. everything works now. but i do have a desktop environment that i dont really need. how would i go about removing that, and having the computer load straight into mythtv with a splash screen?

My suspicion would be that you weren't filling out the page that asked for password and hostname to your master backend and actually testing the connection.  Does this sound accurate?

---

### Post by gsrcrxsi on 2007-11-05
im pretty sure i filled all that out.

does the frontend only install have the desktop environment? or just a splashscreen and right into myth? id rather have the latter, and i could try to reinstall it again and make sure i fill it all out 100%

---

### Post by superm1 on 2007-11-05
> **gsrcrxsi said:**
> im pretty sure i filled all that out.

does the frontend only install have the desktop environment? or just a splashscreen and right into myth? id rather have the latter, and i could try to reinstall it again and make sure i fill it all out 100%
Xfce is still installed for a frontend install.  As much as I'd love to get this bug nailed, I understand reluctance to want to redo an installation :(.

---

### Post by volkswagner on 2007-12-07
same problem here.  Has anyone successfully completed an advanced install.  I would like to set up a slave backend/frontend.

The error I get is the same "Installer crashed"  I see a bug report has been filed.

I performed manual partition, there was a warning because my windows boot partition is a fat16 and installer says windows may not like.  I procedeed with ignore.

I did not set up a remote, I manually entered mysql info and did not perform a test as my server is not up(another problem).

I see a bug has been reported [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/164979]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/164979")

I don't know how to attach log file so here is /var/log/syslog
```

Dec  7 20:44:26 ubuntu syslogd 1.4.1#21ubuntu3: restart.
Dec  7 20:44:27 ubuntu kernel: Inspecting /boot/System.map-2.6.22-14-generic
Dec  7 20:44:27 ubuntu kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Dec  7 20:44:27 ubuntu kernel: Symbols match kernel version 2.6.22.
Dec  7 20:44:27 ubuntu kernel: No module symbols loaded - kernel modules not enabled.
Dec  7 20:44:27 ubuntu kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc $
Dec  7 20:44:27 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Dec  7 20:44:27 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usab$
Dec  7 20:44:27 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (rese$
Dec  7 20:44:27 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff70000 (usab$
Dec  7 20:44:27 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007ff70000 - 000000007ff72000 (ACPI$
Dec  7 20:44:27 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007ff72000 - 000000007ff93000 (ACPI$
Dec  7 20:44:27 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007ff93000 - 0000000080000000 (rese$
Dec  7 20:44:27 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (rese$
Dec  7 20:44:27 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (rese$
Dec  7 20:44:27 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (rese$
Dec  7 20:44:27 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (rese$
Dec  7 20:44:27 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (rese$
Dec  7 20:44:27 ubuntu kernel: [    0.000000] 1151MB HIGHMEM available.
Dec  7 20:44:27 ubuntu kernel: [    0.000000] 896MB LOWMEM available.
Dec  7 20:44:27 ubuntu kernel: [    0.000000] found SMP MP-table at 000fe710
Dec  7 20:44:27 ubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 524144) 0 entries of $
Dec  7 20:44:27 ubuntu kernel: [    0.000000] Zone PFN ranges:
Dec  7 20:44:27 ubuntu kernel: [    0.000000]   DMA             0 ->     4096
Dec  7 20:44:27 ubuntu kernel: [    0.000000]   Normal       4096 ->   229376
Dec  7 20:44:27 ubuntu kernel: [    0.000000]   HighMem    229376 ->   524144
Dec  7 20:44:27 ubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
Dec  7 20:44:27 ubuntu kernel: [    0.000000]     0:        0 ->   524144
Dec  7 20:44:27 ubuntu kernel: [    0.000000] On node 0 totalpages: 524144
```

---

### Post by volkswagner on 2007-12-07
Finally figured how to capture text in error window.  Needed to use rt. click not ctr>+C



Installer Crashed

```
We're sorry; the installer crashed. Please file a new bug report at https://launchpad.net/ubuntu/+source/ubiquity/+filebug (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/syslog and /var/log/partman:


Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 212, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 207, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 65, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 252, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 330, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/mythbuntu_install.py", line 288, in <module>
    install.run()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 100, in run
    self.configure_mythbuntu()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 179, in configure_mythbuntu
    raise InstallStepError("MythbuntuApply Debconf Xfer failed with code %d" % ret)
InstallStepError: MythbuntuApply Debconf Xfer failed with code 255
```

---

### Post by volkswagner on 2007-12-08
Does anyone know if the backend needs to be up and running to do an advanced install for secodary backend?

here is my var/log/partman after crash

```

/bin/partman: *******************************************************
/lib/partman/init.d/01unsupported: ********************************************$
/lib/partman/init.d/30parted: *************************************************$
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo

```

---

### Post by superm1 on 2007-12-08
> **volkswagner said:**
> Does anyone know if the backend needs to be up and running to do an advanced install for secodary backend?

here is my var/log/partman after crash

```

/bin/partman: *******************************************************
/lib/partman/init.d/01unsupported: ********************************************$
/lib/partman/init.d/30parted: *************************************************$
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo

```
Yes the primary backend *must* be up and working to do an advanced install w/ secondary backend or frontend.

---

### Post by volkswagner on 2007-12-08
Thanks for the reply, this may need to be added to the documentation, and install instructions.  I am not sure the proper way to inform the folks at launchpad.  I did however add my comments to the thread there confirming the need for master to be running.  On my way to whole house DVR.

Since I am not The OP I would not mark as solved.

Cheers

---

