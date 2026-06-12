---
title: "Squid Proxy Configuration"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by Oxwivi on 2010-08-17
Hi all,

I've been cooking by brains off in all possible manner to understand how to configure Squid. I don't care what the settings are, I just want to use Squid for all my connections. I did read somewhere you've add some lines after the ACL section, but where the hell is this section?! These guides tells you to add lines but not where.

I request the default configuration file edited to have all the connections through Squid or at least a comprehensive guide which tells me to post what and where.

Thank you very much!

---

### Post by Bertus_Nel on 2010-08-17
Why dont you just browse to  https://localhost:<Port> Go to Squid Proxy Server - Access Control - the you will see you ACL - add or delete as you wish - restart squid and you should be set to go.;)

---

### Post by Oxwivi on 2010-08-17
Do I type that in Firefox? I'm not that technical yet, I need straightforward instruction to just let Squid take over all my connections. TT_TT

---

### Post by Oxwivi on 2010-08-17
What is the address and ports I should use to route my traffic through Squid? That info alone would be enough to get me going, thanks!

---

### Post by lovelyvik293 on 2010-10-23
You have to put the ip address of the server on which you installed the squid. and port should be the one which you configured in squid.conf.
Default port is 3128.

---

### Post by Oxwivi on 2010-10-23
Thanks, but looks like I no longer need to use it... Forgotten about this completely.

---

