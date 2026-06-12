---
title: "setting up work loopback server"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by playinpearls on 2010-03-24
Hi all, 


n00b here...of course..

I'm setting up a loopback server for work related testing.

I have a small program that needs to be executed through telnet from about 200 ip's on the  same network. 

On the server, i have to set a static ip, enable telnet login, and place my 2 program files in the appropriate folders so it will run. 

I have been on this for 2-3 days and haven't gotten far. 

my /etc/Network/interfaces file is this...

auto lo
iface lo inet loopback

~ ~                                                                         
~                                                                         
~                                                                         

the rest of terminal is filled up with these, and it states that the file only has 32 characters. I dont know if this is a privilege issue or not...

i've read several threads on telnet, and lots of arguments about ssh, but i can't run ssh, so i need to enable telnet. There is not a security issue...i run a private network where the only valuable resource would probably be the text file with my ip address on it. Its also accessed by people that have very limited networking knowledge and no linux knowledge...

so...
set static ip
setup telnet server...

any takers?

---

### Post by playinpearls on 2010-03-24
i also was reading a thread about a static ip constantly getting reset by dhcp and the network manager. it gave a command about removing the network manager so i did it...(sudo apt-get remove --purge network-manager*)

let me know if i should reinstall that...

---

### Post by playinpearls on 2010-03-24
got'em both....disregard

---

### Post by Iowan on 2010-03-24
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") - or still not working? BTW, Network Manager has (had?) a way to set a static address.

---

