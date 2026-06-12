---
title: "Errors logging in with NIS"
date: 2012-08-02
forum: Networking &amp; Wireless
---

### Post by jeraldamo on 2012-08-02
Ok, so I have never set up a NIS network before, so before I dive head first into setting up all my labs with it, I thought that I would dabble with it by creating a single Master server and a single client.

I already have everything set up by following [these instructions]("https://help.ubuntu.com/community/SettingUpNISHowTo") verbatim. Like I said, I have a single server box and a single client box, both are running 10.04 LTS Desktop Edition (32 bit). 

I then added a user to the server and updated the maps with ```
sudo make -C /var/yp
```. As far as I can tell that was successful.

When I go to log into the user account from the client it first acts successful. Then I get three consecutive popups that say:

*"could not update ICEauthority file"*

[I]"There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"

[/I]
[I]"**Nautilus could not create the following required folders: /home/user/Desktop, /home/user/.nautilus.**
Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.[/I]"

I then get the purple clouds background with no apparent gui. If I spring a terminal, followed by a whoami it says that the current user is a non-privileged user account on the client machine.

I've checked ownership of the aforementioned files and they are owned by the user.

My question is is this a client or a server issue, and is it even related to NIS. My hunch is that it is because if I am on the server machine I can log into the user just fine, it is only when I attempt to log into the user from the client machine that I get these errors.

Any help, suggestions, or guidance would be greatly appreciated. Thanks!

Jeraldamo

---

### Post by jeraldamo on 2012-08-06
If I did not state the problem in a clear manner or if you need more information please don't hesitate to ask...

Thanks,
Jeraldamo

---

