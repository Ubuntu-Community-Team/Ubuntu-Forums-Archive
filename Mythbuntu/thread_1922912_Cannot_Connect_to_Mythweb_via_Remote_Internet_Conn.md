---
title: "Cannot Connect to Mythweb via Remote Internet Connection"
date: 2012-02-09
forum: Mythbuntu
---

### Post by ooboontwo on 2012-02-09
Hello everyone,

I have done extensive research about this, searching and googling everywhere. I haven't been able to find a solution that has worked for me, so I am posting here.

I want to be able to connect to mythweb from the internet using my WAN ip.

Here's the details:
1. I am running mythfrontend/backend on a MediaPC in my living room
2. I can access mythweb from another computer through my home network
3. I am unable to access mythweb using my MediaPC WAN ip outside my home network
4. I can access my MediaPC (Remote Desktop) using VNC and its WAN ip
5. I have port forwarding enabled on my home router, Port 80 forwards to 192.xxx.x.x (which is the local IP address of my MediaPC, of course)

When I type in "MY.WAN.IP.HERE/mythweb" in my web browser from outside my home network it takes forever, does nothing, and finally times out.

Is my ISP blocking port 80? If so, how would I configure another port (like, 8080) to forward to port 80 (thereby bypassing the ISP block)? Is that Port "Triggering" rather than Forwarding? I've never done anything like that before... pardon my ignorance.

Any suggestions are greatly appreciated, and I will be happy to supply any further information necessary in order to resolve this issue.

I really want to watch TVz0rz while I am awayz on Business/vacation tripz, etc!!!!!!!!!!!

Cheers,
Cody

UPDATE: I have solved this problem thanks to help on these forums and google.

Here's how I did it:

I connected to my Media PC using SSH. To do this you have to have SSHD running on the target computer (my MediaPC) and SSH installed on the other computer (my laptop). Then, in terminal, you write something like this:

```
sudo ssh user@remote.comp.ip.here
```

This will give me remote access to my MediaPC. However, I first had to open port 22 on my home router. I did this using port forwarding, which seems secure enough. So, if this command does not work outside of your home network you need to make sure port 22 is open on your home router.

You can use a LAN or WAN ip address with SSH. Obviously, if you are outside your home network you will have to use your WAN ip. This is what I have been doing.

Another neat (but unrelated) trick is to use the "-Y" command with SSH. This allows you to open X (GUI) programs through SSH. It would look like this in terminal:

```
sudo ssh -Y user@remote.comp.ip.here
```

Again, this is irrelevant to getting mythweb working, but it is a cool feature!

Now, once you can connect to your computer remotely you are ready to get mythweb working. What you need to do is use the command "-L". I used the instructions here: [http://www.mythtv.org/wiki/MythWeb_ssh_tunnel_howto](http://www.mythtv.org/wiki/MythWeb_ssh_tunnel_howto)

In the end, my terminal code looks like this:

```
sudo ssh -L 80:localhost:80 user@xx.xx.xx.xx
```

If this works, and you successfully connect, you should be able to open the web browser and go to: localhost/mythweb and VOILA! see Mythweb running remotely over the internet on another computer!

I hope this brief tutorial helps someone else. I feel nerdy in such a good way for having accomplished this feat of networking!!

Thanks again everyone who helped.

Cheers,
Cody

---

### Post by nickrout on 2012-02-09
> **ooboontwo said:**
> Hello everyone,

I have done extensive research about this, searching and googling everywhere. I haven't been able to find a solution that has worked for me, so I am posting here.

I want to be able to connect to mythweb from the internet using my WAN ip.

Here's the details:
1. I am running mythfrontend/backend on a MediaPC in my living room
2. I can access mythweb from another computer through my home network
3. I am unable to access mythweb using my MediaPC WAN ip outside my home network
4. I can access my MediaPC (Remote Desktop) using VNC and its WAN ip
5. I have port forwarding enabled on my home router, Port 80 forwards to 192.xxx.x.x (which is the local IP address of my MediaPC, of course)

When I type in "MY.WAN.IP.HERE/mythweb" in my web browser from outside my home network it takes forever, does nothing, and finally times out. that should work BUT mythweb is very insecure. What I do is run an ssh tunnel via putty on my work computer. works well > 

Is my ISP blocking port 80? If so, how would I configure another port (like, 8080) to forward to port 80 (thereby bypassing the ISP block)? Is that Port "Triggering" rather than Forwarding? I've never done anything like that before... pardon my ignorance.

Any suggestions are greatly appreciated, and I will be happy to supply any further information necessary in order to resolve this issue.

I really want to watch TVz0rz while I am awayz on Business/vacation tripz, etc!!!!!!!!!!!

Cheers,
Cody

Can you speak English please? Unless you have a very fast internet connection you will not be able to watch much, except over the flash player in mytheb.

---

### Post by jdroflet on 2012-02-09
ooboontwo - disable that internet router forwarding to the media server right away. You're home computers and media files are at risk.
As nickrout says Mythweb security is not very secure and is for internal trusted networks only. 

Yes ISP's may be blocking port 80, usually its buried in the end user agreement that you're not allowed to run a server on port 80 on your client connection.

Also as nickrout says look into doing port forwarding over ssh to the mythbox.  Try a google on ssh port forwarding to mythweb 
Your ISP may also block the standard port 22 for ssh but you can set it to tunnel via a different port on the external connection. 

John

---

### Post by ooboontwo on 2012-02-10
OK, so I can connect to my MediaPC using ssh on my laptop but how do I connect to mythweb? I have a terminal interface, but no graphics (X). Where do I go from here?

EDIT / UPDATE: OK, I have X working now through SSH (thanks Google!), but I am still unsure exactly what the most efficient way to stream video to my laptop is going to be. I can open mythfrontend through ssh but the video doesn't play... which makes sense I guess... sort of...

I can access my HDD, so I could copy a file over to my laptop, but that isn't streaming of course.

I'm just curious how people use SSH with MythTV; what is the best way to stream video from my MediaPC to my laptop using SSH?

Thanks,
Cody

---

