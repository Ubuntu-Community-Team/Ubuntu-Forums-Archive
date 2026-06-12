---
title: "ssh - matlab run in background"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by evan54 on 2010-03-17
using: karmic coala ubuntu 9.10

I'm trying to run a matlab script from the terminal on a remote server and then close the terminal and still have it running.

the commands I use are:

1) to log onto server                 : ssh -X user@server
2) to cd to right path                 : cd right/path
3) to run script                           : nohup matlab -nodisplay -nojvm < script.m > output.txt
4) to log off                                 : exit
5) to exit terminal                      : exit

The 3rd command works fine if i don't quit. So I can see the output.txt and it is loading and also the files that the script should output are created. However once I quit and then check back I don't find the additional files i'd expect and it seems to quit.

I thought the nohup command would fix this which is why it's there in the first place...

any help on this would be great...

---

### Post by evan54 on 2010-03-24
So figured out what was wrong. I was going to my home directory on the server which isn't local to any machine (from what i understand) so whenever I logged out a "token" (not sure what that was) was thrown or lost or smth like that. I was told i could either use keeptoken (or something like that) to keep the token and that would allow me to log off without loosing the session or i could run things from a local (to the particular server machine so i had to log into username@server-machine1 instead of username@server) folder. This worked fine but you had to know/remember which machine you'd log into as the username@server could potentially log you on a different machine.

---

