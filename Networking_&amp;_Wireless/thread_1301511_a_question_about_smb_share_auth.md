---
title: "a question about smb share auth"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by ubuscout on 2009-10-26
Hi,

I'm trying to setup an "ubuntu standard desktop" (9.04) in my office, a mix enviroment (an fileserver linux samba, windows 2003 bdc and many windows 2k/xp workstation). My idea is an step-by-step replacement of windows WS as many possible :)

So here one of the first problem I faced is this:
I've joined my (virtualbox) ubuntu and another laptop in my AD windows domain, following  Ubuntu instruction . So it seem ok almost everything, joined to domain was ok,and my login authentication seem doing fine, I perform it with 'MYDOMAIN\myuser" without problem.

When I browsing my network and clikking on my server share it show me a prompt asking me a password ?!?  :confused: ...here the question... 

I think, I am just authenticated in domain ! ...why am I prompted to
insert password again ?!? (Please note, of course if I insert password I
get my share without problem... but I think I must not need do it too
isn't it ?)


The command 'klist' give me this output:
----
Ticket cache: FILE:/tmp/krb5cc_10672

Default principal: [email]myuser@MYDOMAIN.COM[/email]


Valid starting     Expires            Service principal

10/26/09 10:06:43  10/26/09 20:06:42  krbtgt/MYDOMAIN.COM@MYDOMAIN.COM
	renew until 11/02/09 10:06:43

10/26/09 10:06:42  10/26/09 20:06:42  UBUDESK$@MYDOMAIN.COM
	renew until 11/02/09 10:06:42





Kerberos 4 ticket cache: /tmp/tkt0

klist: You have no tickets cached
----

...it seem to me, I'm just granted... isn't it ?!?

Samba is just Pam aware, so why this authentication request ?!

thx in advance :)

---

### Post by ubuscout on 2009-10-28
...a polite bump... ;)

---

