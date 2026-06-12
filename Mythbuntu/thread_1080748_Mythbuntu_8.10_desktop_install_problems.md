---
title: "Mythbuntu 8.10 desktop install problems"
date: 2009-02-25
forum: Mythbuntu
---

### Post by Panhead Bill on 2009-02-25
Attempting to set up front end only, Nvidia driver, link to existing backend.  Results: Near the end of the install I get an error screen.  "Application Problem - sorry the program UBIQUITY closed unexpectedly"

Attempted fixes: 
1)  I used synaptic to load ubiquity; then package manager lists several updates needed but cannot download Base-files. (Debian-base system miscellanious files size 63KB)
2)  I tried a fresh copy of Mythbuntu desktop 8.10; same result.
3)  Eliminated Nvidia driver option; same result.
4)  Tried standard install - no options.  Install almost works but of the two security updates the update manager noted only one downloaded.  "An error occured  W. failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_4.0.4ubuntu](http://archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_4.0.4ubuntu) 2.1_i386.deb  404 not found [ip:91:189:88:40:80]"

  I then hit "check" in the package manager and 176 updates loaded and were installed. After that the update manager indicates that all is current.
  The system seems to work but gives me a recurring icon to restart, and the network icon randomly indicates that the network is connected and then disconnected (even though Firefox connects to several sites while "disconnected")

Any ideas why I can't seem to get Mythbuntu desktop 8.10 to install as a frontend only?

---

### Post by pjbgravely on 2009-02-26
Did you check the disc for errors? It is one of the boot options.

You won't see the network icon when the frontend is running so if it is just a bug ignore it.

---

### Post by Panhead Bill on 2009-02-26
Yes both disks were checked for mdsums and checked for errors.

Again the question is why does the "vanilla" install more or less work, but the variation I want, front end only, end in an ubiquity error?

New info: attempts to run from cd go most of the way through the setup then loop back to the initial "Live or install" screen.

---

