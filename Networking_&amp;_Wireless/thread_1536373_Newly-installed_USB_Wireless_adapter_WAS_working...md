---
title: "Newly-installed USB Wireless adapter WAS working..."
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by mathwizard44 on 2010-07-22
I have an old Gateway desktop computer which is now running Xubuntu. When I moved it to my office I installed a Linksys USB Wireless Adapter, model WUSB12 version 1. This was not accomplished without incident--I installed ndisgtk (I already had ndiswrapper) and changed some settings (which I cannot remember right now) but after about an hour it worked. I loaded up pages in Firefox, checked out Lynx, and basically had a connection.

But then the next time I turn it on the internet does not work anymore. I can see the wireless router connecting to the network, and showing me a strong connection. But loading up a page in Firefox does not work. Neither Lynx nor wget work, either.

And something else that's worth mentioning is that if the USB wireless adapter is plugged in before my system boots up, NetworkManager (which I assume is what that networking icon at the top right is called) will report that there are no network devices available, even though ndisgtk (or "Windows Wireless Drivers") will report that the hardware is present (after telling me in a popup that it was "unable to see if hardware is present"). When I plug in the adapter after my computer has turned on and I've logged in, then I get the strong connection but no internet.

I am typing this on a laptop right running another OS (OK, fine, it's Windows XP) right next to my Gateway and the wireless works well over here. What will I have to check? I'll post the output of any commands you'd like me to try that may lead to a solution. To be clear, the internet was working right after I installed the adapter, but not since.

Thanks in advance for any assistance.

MW

---

### Post by mathwizard44 on 2010-07-23
I just noticed something when I saw my user profile. Lest you think of asking me to upgrade to the latest Ubuntu, let me say that I am running 9.10, which isn't the newest, but it isn't 6.06 either. But if that fixes it, then I'll do it. Shouldn't there be another way, though?

---

