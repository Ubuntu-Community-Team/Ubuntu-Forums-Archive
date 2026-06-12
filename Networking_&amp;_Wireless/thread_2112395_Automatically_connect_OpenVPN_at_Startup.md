---
title: "Automatically connect OpenVPN at Startup"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by AwaitingUserInput on 2013-02-04
Ubuntu 12.10

I pay for a VPN service that I connect to using OpenVPN.

Oftentimes, I start my computer and forget to connect to the VPN.

Is there a way to have it connect to my VPN upon startup by default?

I'm pretty new to linux and did some searching and found some answers that all involved writing shell scripts, which is a bit over my head, so I'm hoping there's an easier way.

Thank you.

---

### Post by ahallubuntu on 2013-02-04
~

---

### Post by AwaitingUserInput on 2013-02-04
Wow! You did a great job explaining! Thanks so much. I did what you said and it worked on the first try. How did you learn all this stuff?

And as a more general question, which 1 aspect of your post should I read about a little more to gain general knowledge about how my Ubuntu machine runs? Should I learn about UUIDs?

Thanks again for the help.

---

### Post by ahallubuntu on 2013-02-04
~

---

### Post by demented_demigod on 2013-02-09
Despite having hung around the forums for a while and having a pretty good handle on ubuntu I still chase answers for seemingly simple stuff every now and again.

ahallubuntu, this is one of the most pleasant, easily understood forum posts/replies I've ever seen, thank you :)

Cheers,

Demented

---

### Post by Whoopie on 2013-02-10
You could wait for Ubuntu 13.04 where network-manager has a new feature to start a VPN connection as secondary connection.

Or use the AUTOSTART feature in /etc/default/openvpn.

---

### Post by AwaitingUserInput on 2013-07-06
Ahallubuntu's answer disappeared from the thread for some reason. I was able to grab a copy from Google's cache. Here it is:

The bad news is: you're going to need a shell script to do it. The OpenVPN plug-in for Network Manager has a "Connect Automatically" option, but as far as I know, it's always been broken (for years) and still broken in 12.04. I'm almost certain it's still broken in 12.10, which I don't use.

 The good news is: it's not that hard, and you can copy an existing script and modify it. You don't have to start from scratch. In fact, it's going to wind up being a single line script. (This assumes you use Network Manager for managing your networks, the way most Ubuntu users do.)

 I have done something similar before. But this should work for you:

[http://ubuntuforums.org/showthread.php?t=1968436](http://ubuntuforums.org/showthread.php?t=1968436)

 Basically, three things you have to do:

 1. Figure out the UUID of your VPN connection. "UUID" is basically a "randomly-created ID number" that Network Manager uses to keep track of all your different network connections. It's a long number but once you find it you can simply copy-and-paste it.

 Find the UUID using this command:

```
nmcli con list | grep -i vpn
```

The UUID is the second column with the letters, numbers and dashes. Mine is:

 > MyVPN 104c28ec-9a22-4615-9110-6a4839a1386a vpn Mon 04 Feb 2013 09:41:44 AM PST 

So my UUID is 104c28ec-9a22-4615-9110-6a4839a1386a .

 2. Start the connection in a terminal. To start mine in a terminal I'd type:

```
nmcli con up uuid 104c28ec-9a22-4615-9110-6a4839a1386a
```

Try it now: start a terminal, figure out the UUID and (when you are not connected to your VPN), and do the "nmcli con up uuid " with your UUID after it. That way, you can see that you can bring up your VPN that way.

 3. Set this to run at startup and forget about it. Go to the * menu (with Shut Down, etc.), choose Startup Applications, and add the nmcli command above (whole thing with the UUID). Click "Add" and in the name type "start my OpenVPN" and in Command put the whole nmcli line you used above. Click "Add" again. Now, reboot and try it!

---

