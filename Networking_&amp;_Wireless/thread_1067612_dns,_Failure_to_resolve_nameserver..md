---
title: "dns, Failure to resolve nameserver."
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by exploding5heep on 2009-02-12
I've installed Ubuntu 8.10 on a few computers I have, but have been having trouble with dns servers. Many lookups are failing for a reason I don't understand. The /etc/resolv.conf file gives this error:

# The nameservers listed below may not be recognized.
nameserver 167.142.225.5

What causes this issue? I am currently on a college campus network. I know of a few other Ubuntu users on the network who also have the same dns issue I do. What I would like to do is figure out why Ubuntu isn't interacting with the dns servers correctly. Windows/OS10 computers on the network don't have the issue.

I can ping the 167.142.225.5 server without issue. The average time was ~7ms if that is relevant.

I've tried using the opendns servers, which work, but I haven't been able to get firefox's awesome bar restored to full functionality when doing that, which for me is almost worse than the dns issue. Is there a way to do that? I looked for a way for awhile but didn't succeed.

Thanks ahead of time for any help.

---

### Post by jonobr on 2009-02-12
Recommend you install wireshark and trace what is happening at a packet level with your dns lookup.

If you want you could post it here,
If you prefer not to out of security, you could do a wireshark on the windows machine that works and compare the DNS query to the ubuntu machine.

Stare and compare between the two should show the differences.

---

### Post by Ptero-4 on 2009-02-12
You could also compare to the Macs and try and replicate the settings as best as you can (is easier b/c OSX is kinda similar in cli stuff to linux and you´ll only need some small adjustments).

---

### Post by ugm6hr on 2009-02-12
> **exploding5heep said:**
> I've tried using the opendns servers, which work, but I haven't been able to get firefox's awesome bar restored to full functionality when doing that, which for me is almost worse than the dns issue. Is there a way to do that? I looked for a way for awhile but didn't succeed

What effect does OpenDNS have on FireFox?  My "intelligent search" address bar works fine with openDNS.

---

### Post by exploding5heep on 2009-02-12
An example of how it doesn't work correctly is whenever I enter something like "ups" instead of being taken to the ups website, I'm taken to an opendns search results page, and then have to click to get to the actual ups site. As far as I can tell, opendns always gives some sort of return after a lookup, even if the lookup wouldn't normally give anything, which prevents the address bar from doing any of its behaviors that are based on a failed lookup. 

I will give wireshark a try tomorrow.

---

### Post by Ptero-4 on 2009-02-12
The reason for the "awesome bar" behavior is that OpenDNS automatically "catches" incorrectly formed URL´s (OpenDNS expects the address bar to be used only to input URL´s, it doesn´t recognize yet if the address bar have "smart keywords" capalities) to prevent the user from falling in most of the intentionally malformed "URL´s" used by con artists and malware writers to infect your PC, steal your data and do other bad stuff.

---

### Post by ugm6hr on 2009-02-13
Indeed. This is a deliberate security benefit of OpenDNS, but also allows OpenDNS to earn money by search referrals.

---

### Post by jonobr on 2009-02-13
Agree to all above, Opendns earn their money this way.
Doing wireshark wont help you, but knowing wireshark anyway is still sueful

Cheers

---

