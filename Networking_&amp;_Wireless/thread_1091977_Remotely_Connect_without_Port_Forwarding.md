---
title: "Remotely Connect without Port Forwarding?"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by jflash on 2009-03-09
I just set up a server for my high school robotics team running subversion for source code control. We've got it running perfectly in our meeting space where we're all on the same LAN. However, when we go to competition we'd like to not have to drag the machine with us. The problem I'm running into is that we're behind at least one router (possibly more at the central office level) that I don't have access to in order to forward the necessary points to access the box from the outside world. While I could probably get it done by the school system IT department, they aren't exactly known for speed or competency. 

My question is what solutions are available short of going through the normal channels? What I had in mind was some sort of setup akin to that used by LogMeIn, etc. where the server initiates the connection with a remote machine which handles the connection from remote clients (I'm not opposed to using my home computer for this). I'll also mention that there are a limited number of computers that will be accessing the server, all of which will be known and available beforehand. Therefore, if any client-side software is needed that's not at all prohibitive. Thanks in advance for any help, and if any additional information is needed let me know.

---

### Post by Woodsyx on 2009-03-09
Hamachi might fit your needs, it sets up a vpn between the host and you and can be run on linux, osx, and windows.

---

### Post by jflash on 2009-03-09
Am I correct in assuming with Hamachi the server would initiate the connection?

EDIT: I take that back after actually looking into it. Looks like it should work, but if anyone has other ideas I'd appreciate them. Thanks!

---

### Post by kevdog on 2009-03-09
ssh reverse tunneling perhaps?

---

