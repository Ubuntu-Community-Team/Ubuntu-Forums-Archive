---
title: "NetworkManager does not call /etc/network/if-pre-up.d scripts"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by JoeDuncan on 2009-03-01
I've been trying to get a script to trigger on the "pre-up" phase of network configuration, however, NetworkManager doesn't seem to call it's dispatcher for "pre-up" events.

I'm running Ubuntu 8.10 with all the latest updates installed.

Everything I have found says that NetworkManager calls the script "/etc/NetworkManager/dispatch.d/01ifupdown" for all post-down, down, pre-up and up events when establishing network connections. Indeed in that script I found the following:

```

case "$2" in
    up)
        exec run-parts /etc/network/if-up.d
	;;
    down)
        exec run-parts /etc/network/if-down.d
	;;
    pre-up)
        exec run-parts /etc/network/if-pre-up.d
	;;
    post-down)
        exec run-parts /etc/network/if-post-down.d
	;;
esac

```

Which seems to indicate that this script is intended to call the scripts in the /etc/network/if*.d under the appropriate circumstances. However, none of the scripts I put in /etc/network/if-pre-up.d ever got called, so I added the following line to the top of the file:

```

logger -t $0 "called with $1 $2"

```

Where $0 is the name of the script, $1 is the network interface and $2 is the network event.

After bringing some network connections up and down, I checked the logs, and NetworkManager doesn't seem to be calling "/etc/NetworkManager/dispatch.d/01ifupdown" for either "pre-up" or "post-down" events. The only entries show up for "up" and "down" events.

Is there something I am missing or that I have not configured properly? Everything I have read elsewhere suggests that NetworkManager should call the dispatcher for all network phase events.

For example post #3 here:

[http://ubuntuforums.org/showthread.php?t=816541&highlight=networkmanager+if-pre-up](http://ubuntuforums.org/showthread.php?t=816541&highlight=networkmanager+if-pre-up)

Here:

[https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses](https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses)

and in the changelog here (for version 0.5.1-0ubuntu12):

[https://launchpad.net/ubuntu/+source/network-manager](https://launchpad.net/ubuntu/+source/network-manager)

So what's the problem?

Thanks!

---

### Post by JoeDuncan on 2009-03-02
Posted a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/336736](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/336736)

However, any help on this would still be greatly appreciated!

Thanks!

---

### Post by lswb on 2009-03-02
Make sure the scripts have been chmod +x and are owned by root.

---

### Post by JoeDuncan on 2009-03-02
Yeah, that was the very first thing I did. 

All ownerships and permissions check out ok. If either were wrong, I should at least still see a syslog entry from "/etc/NetworkManager/dispatch.d/01ifupdown" saying it had been called with a "pre-up" phase parameter, and this never happens.

"/etc/NetworkManager/dispatch.d/01ifupdown" is never called with the "pre-up" phase parm, so it never calls "run-parts" on the "/etc/network/if-pre-up.d/" directory in the first place.

It would be a moot point even if the ownerships and permissions were wrong (should at least see it *trying* to call them and then failing).

thanks

---

### Post by lswb on 2009-03-02
I see your bug report was acknowledged today. Guess that needs to be fixed before you can use the if-pre-up.d script. I saw your question about downgrading NM from 0.7 to 0.6. I have both hardy with 0.6.6 and intrepid with 0.7 and there quite a few differences between the 2 versions, including completely different init scripts and helper applications. It might work for running the ip-pre-up.d scripts but break something somewhere else.

What did you want to run from the ip-pre-up script? Maybe there is another way to get results you are looking for.

---

### Post by USD on 2009-04-20
It has been a while since this was posted - is there a solution or progress or what? Thanks.

---

