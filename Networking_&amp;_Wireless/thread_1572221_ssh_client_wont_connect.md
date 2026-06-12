---
title: "ssh client wont connect"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by ductiletoaster on 2010-09-10
Ok so i have a server in which i have setup dyndns setup so that i can use an address such as example.com to connect to my server.

The server has openssh installed and it is configured properly.

What I can do:
```

Connect to server (locally) from linux terminal
Connect to server (locally) from windows putty client
Connect to server (Over Internet) from windows putty client

```

What I can't do
```

Connect to server (Over Internet from linux terminal

```

When I try to connect with terminal via the internet this is the error i get
```

ssh: Connection to host [ADDRESS] port [PORT]: Connection timed out

```

Could it be some settings for the ssh client on linux that is off? Any suggestions would be helpful!
Thank you

---

### Post by perspectoff on 2010-09-10
make sure networking is working on your client linux computer:

sudo /etc/init.d/networking restart

In Lucid I have noticed some funny problems with the DNS cache, which gets reset when I restart networking.

I have had the same problems as you, but it disappears when i restart networking. i haven't stopped to figure out exactly why, yet.

---

### Post by ductiletoaster on 2010-09-10
ok i will try that and post back.

The issue i have is the client is on a laptop which has been restarted several times. and I would assume a machine reboot would more than likely handle you suggestion
I gave it a try any way and sure enough no go!

Thanks though

---

### Post by ductiletoaster on 2010-09-10
Any one?

Ok so i figured it out! I fixed it by moving my server in my network. see diagrams below

Old Network Diagram:
```

INTERNET     <->     GATEWAY     <->     BRIDGE     <->     UBUNTU SERVER
                        |                  |                  (Ethernet)
                   UBUNTU LAPTOP     WINDOWS CLIENT
                    (wireless)         (Ethernet)

```

New Network Diagram:
```

                   UBUNTU SERVER
                    (Ethernet)
                        |
INTERNET     <->     GATEWAY     <->     BRIDGE 
                        |                  | 
                   UBUNTU LAPTOP     WINDOWS CLIENT
                    (wireless)         (Ethernet)

```

And that fixed it. It also fixed my Wake on Lan over internet problem. It seems the bridge was causing some stupid problems.

---

