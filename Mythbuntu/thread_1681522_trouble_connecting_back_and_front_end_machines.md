---
title: "trouble connecting back and front end machines"
date: 2011-02-04
forum: Mythbuntu
---

### Post by swansome on 2011-02-04
I'm trying to setup a basic Mythtv system. I am able to use mostly defaults with the MythUbuntu fresh install and get it working on a single machine. I can do the same thing on the second machine. I get great HD from my silicon dust tuners.

I cannot connect the two machines. Each time I run the remote frontend, it freezes after setting the IP addresses.

I've also tried this with OpenSuse and have the same issue.

Last night I tried fresh again. My backend machine worked fine again with the default install. I then changed the IP address location (2) and it still worked. I recorded again. During that switch, the "test button" saw the other machine successfully.

I tried the other machine. It worked fine. Then I switched to the IP address of the basement machine. Screen went blank. Froze. Upon forcing a reboot, it would not launch frontend again.

I tried a fresh install on this machine - set to "front end only" from the mythbuntu install disk. During setup, there is a "test button" that says it cannot connect to the database and lists the correct password. It will not finish the install.

At this point, it seems like there must be something wrong with my network setup. I have a wireless router with 6 ethernet jacks. I have never done anything with it - it seemed to be just plug and play right from the beginning. Do I need to figure out more details about that or do I perhaps have too old of a router system?

Thanks for helping out an old fart who is a baby in Linux...

---

### Post by nickrout on 2011-02-04
You need to look at your logs and see what they say.

---

### Post by klc5555 on 2011-02-05
> **swansome said:**
> I'm trying to setup a basic Mythtv system. I am able to use mostly defaults with the MythUbuntu fresh install and get it working on a single machine. I can do the same thing on the second machine. I get great HD from my silicon dust tuners.

I cannot connect the two machines. Each time I run the remote frontend, it freezes after setting the IP addresses.

I've also tried this with OpenSuse and have the same issue.

Last night I tried fresh again. My backend machine worked fine again with the default install. I then changed the IP address location (2) and it still worked. I recorded again. During that switch, the "test button" saw the other machine successfully.

I tried the other machine. It worked fine. Then I switched to the IP address of the basement machine. Screen went blank. Froze. Upon forcing a reboot, it would not launch frontend again.

I tried a fresh install on this machine - set to "front end only" from the mythbuntu install disk. During setup, there is a "test button" that says it cannot connect to the database and lists the correct password. It will not finish the install.

At this point, it seems like there must be something wrong with my network setup. I have a wireless router with 6 ethernet jacks. I have never done anything with it - it seemed to be just plug and play right from the beginning. Do I need to figure out more details about that or do I perhaps have too old of a router system?

Thanks for helping out an old fart who is a baby in Linux...

Make sure the master backend has had its MySQL service set to accept remote connections (in the Control Centre). Make sure that the PIN number in the General backend setup page is set to 0000 in both the master backend and the secondary backend.

---

### Post by swansome on 2011-02-05
thanks - i didn't scroll on the setup screen and see that setting - that little check cost me about 4 hours.

idiot

thanks so much for the advice.

---

### Post by zanadu on 2012-06-16
I have this trouble as well. I have checked all of the above and have inserted the correct IP address and other details but receive the message "cannot connect to database".

However....

I am running the master backend on a 64 bit dual CPU  Athlon, and the secondary backend and frontend on a 32bit Intel processor. Does anyone know whether the two systems are incompatible or not? Does the database on the 64 bit machine need another 64bit machine to read it, for I have done everything that seems to be required to connect, but have had no joy.

Later development.

I removed tha secondary backend. --presumably this was not needed, and a connection was made to the primary backend machine. However... I now receive a message informing that the database's TV schema on the backend is newer that  "expected". 

I am operating on Mythubuntu-11.04-i386. which has been updated.
Is there and "i686 " version available?

---

### Post by jlp_engineer on 2012-06-16
My guess would be that the two systems are unaware of their host operating system properties.  For the most part, the MythTV protocol (as well as other basic network protocols) 'should' be blissfully ignorant of whether they come or go to a 32bit or 64bit OS.  :-\"

I am running a 32bit master backend and a 32bit slave backend, with a couple of 64bit remote frontends, no major problems.  I do have one issue, with placing the default storage group on a file system that is non-root, but I am working through the issue, and hope to have it resolved soon.

---

### Post by nickrout on 2012-06-16
> **zanadu said:**
> I have this trouble as well. I have checked all of the above and have inserted the correct IP address and other details but receive the message "cannot connect to database".

However....

I am running the master backend on a 64 bit dual CPU  Athlon, and the secondary backend and frontend on a 32bit Intel processor. Does anyone know whether the two systems are incompatible or not? Does the database on the 64 bit machine need another 64bit machine to read it, for I have done everything that seems to be required to connect, but have had no joy.

Later development.

I removed tha secondary backend. --presumably this was not needed, and a connection was made to the primary backend machine. However... I now receive a message informing that the database's TV schema on the backend is newer that  "expected". 

I am operating on Mythubuntu-11.04-i386. which has been updated.
Is there and "i686 " version available?

of course the 32 bit machine will work with the 64 bit machine.

what is important is having the versions of mythtv match. what versions are you running?

---

