---
title: "Yet another &quot;join Ubuntu to Active Directory&quot; post...."
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by PapaJupe on 2009-04-06
I've tried using Likewise-Open to join my Ubuntu laptop to my companies Active Directory network. After countless days of terminal typing, .conf editing, samba/winbind installing/configuring, and random bouts of excessive beer drinking/hair pulling, I'm about ready to throw in the towel! :evil: Yet, I am SO close to getting there. Now, when I try to join the AD via Likewise (either through the GUI or command line), I get the following:

[B]The configuration stage 'open ports to DC' cannot be completed automatically. Please manually perform the following steps and rerun the domain join:

Some required ports on the domain controller could not be contacted. Please update your firewall settings to ensure that the following ports are open to '*server-name-example1*.*abc.tec.nj.local*':
	88  UDP
	389 UDP
	464 UDP
	123 UDP[/B]

From all I've read, you're supposed to make sure that the "Windows Time" service is running on the Domain Controller (which is a virtualserver, by the way), as this causes the above error.I thought this was the case, as all the above ports are wide open to me, on the network. That, and I even disabled the Multicast DNS Discovery Service on Ubuntu, which has been known to cause conflicts with AD-join process. I'm missing something, and I'm too close to it now to see the issue clearly.

ANY advice... from anybody, please? Where am I going wrong, here?? Looking forward to any and all feedback. Thanks, in advance!

---

### Post by PapaJupe on 2009-04-08
I've answered my own question, and have joined my employers Active Directory through trial and error.

Thanks for the help, all.... :-| I'm out of here.

---

### Post by Barnicle on 2009-04-09
Let me guess, your error lied in your net ads command? Making the -S switch captialize, or something else? I need help as well!

---

