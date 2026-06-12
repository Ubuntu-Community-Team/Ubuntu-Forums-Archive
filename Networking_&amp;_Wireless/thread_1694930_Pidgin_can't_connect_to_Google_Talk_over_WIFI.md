---
title: "Pidgin can't connect to Google Talk over WIFI"
date: 2011-02-25
forum: Networking &amp; Wireless
---

### Post by insecure hyena on 2011-02-25
Hi guys let me report a problem I'm facing right now.
As the title of the thread explains I can't connect to my Google Talk account when on WIFI.
I've had the same problem with the MSN protocol and in that occasion I've resolved simply allowing (ticking) using the http method.
Is there a similar workaround for the XMMP protocol or it's a common and known problem (or bug) of Pidgin?

P.S: I ask this question here cause I didn't find anything on the Web regarding this problem...probably cause my poor searching ability. :(

---

### Post by zenwalker on 2011-02-25
Does this same with empathy as well?

---

### Post by insecure hyena on 2011-02-25
I didn't tried and sincerely I don't have empathy installed, sorry :(

---

### Post by wookiecalling on 2011-02-25
Not sure if this will fix the issue, but a suggestion would be to use open dns or a similar service when on wireless, might resolve it.

---

### Post by insecure hyena on 2011-03-28
Here I am after a couple of weeks...sorry my delayed response.
I'd never use opendns and sincerely I don't know how to use it.
Maybe there's just an option in pidgin?
I don't know and that's why I'm asking for help to anyone has the same problem as I.
So for know I leave this tread open...hope is last to die :(

---

### Post by itsjustarumour on 2011-05-02
Not much help, just commiserations I'm afraid - but I've got the same problem.  Fresh install of 11.04. I've been using Pidgin on every installation of every version of Ubuntu since 6.04 and I've never known this problem.  Just sticks on "Connecting..." forever  :(

Weird.

---

### Post by itsjustarumour on 2011-05-02
> **insecure hyena said:**
> Here I am after a couple of weeks...sorry my delayed response.
I'd never use opendns and sincerely I don't know how to use it.
Maybe there's just an option in pidgin?
I don't know and that's why I'm asking for help to anyone has the same problem as I.
So for know I leave this tread open...hope is last to die :(

OK, think I've found the answer - theres a setting missing that used to be filled in automatically.

Open Pidgin and go to "Accounts", then "Manage Accounts".
Highlight your GMail account, hit "Modify", then select the "Advanced" tab.
Where it says "Connect server", just add "talk.google.com" (without the quotes).
Restart Pidgin, accept the certificate and hopefully that should work  :)

---

### Post by insecure hyena on 2011-05-19
Man let me say sorry for my incredible late response but I was really busy in these last months.
But ehi, you get it!!!
I've done like you said and in addition I've changed the port from the standard 5222 to 80 (the net that I use to connect to the Internet doesn't permit to pass through the standard port) and now I'm able to use Pidgin to chat via my Google Account :D!!!
So lets mark this discussion as SOLVED!!!
And again thank you very much mate!!!:guitar:

---

