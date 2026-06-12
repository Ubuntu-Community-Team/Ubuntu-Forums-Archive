---
title: "SSH and FoxyProxy - bringing a browser session from B to A via X"
date: 2012-12-05
forum: Networking &amp; Wireless
---

### Post by l0w on 2012-12-05
Hi All,

I shall try and be brief. English is my second language, so please forgive the lack of syntactic fluency.

I have done lots of researches but could not find a suitable article (perhaps because I am not using the appropriate search string). I would love an easy ready-made solution, however I am also keen on learning this stuff so I would be happy if someone could at least provide me a pointer.

I'll divide this into two categories: what I am currently doing and what I would like to do but have failed.

Two boxes running Ubuntu 10.04 - Box A (SSH client, Firefox, FoxyProxy) --> Box B (Running a security application - Apache port 8080)
    In order to bring the security app that is running on Box B to my Box A, I connect from A to B in those steps:
        Step 1: 
            Command:
                [ssh -D 1080 <user>@<Box_B_IP>]
        
        Step 2:
            I would launch my local Firefox (running under Box A's) and, having FoxyProxy installed and configured to listen on port 1080, I make this my default proxy.
            
        Step 3:
            I then simply type the server IP on my local browser (Box A's) specifying the port the application is listening on: 8080
[https://<Box_B_IP>:8080]
            
This enables me to run the security application running under Box B as if it were sitting on my own client (Box A). This is all great except for the fact that my Box B is open to the world (OK there are iptables and firewalls, but that's beyond the point). 

Thus, what I would like to do is to have a third box on the game, a 'jump' box in between Boxes A and B (call it Box X), so I can configure the iptables in Box B to only accept traffic coming from Box X, like this:
    A --> X --> B
    
My assumption is that from Box A I should SSH to Box X using a certain parameter to then SSH into Box B using another parameter to bind the ports and be able to run the security application that runs in B to A via X. 

I tried all combinations of parameters like -D and -L and port bindings that my dumb-*ss brain could think of.  

Any inputs would be highly appreciated.

Cheers, 

l0w.

---

