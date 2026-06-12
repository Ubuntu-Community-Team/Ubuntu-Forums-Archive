---
title: "x11vnc question"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by DexterLB on 2009-07-02
Can I make x11vnc execute a command when a viewer connects and another command when a viewer disconnects?

---

### Post by krunge on 2009-07-02
> **DexterLB said:**
> Can I make x11vnc execute a command when a viewer connects and another command when a viewer disconnects?
Yes, see the -accept, afteraccept, and -gone options:
```


-accept string         Run a command (possibly to prompt the user at the
                       X11 display) to decide whether an incoming client
                       should be allowed to connect or not.  "string" is
                       an external command run via system(3) or some special
                       cases described below.  Be sure to quote "string"
                       if it contains spaces, shell characters, etc.  If the
                       external command returns 0 the client is accepted,
                       otherwise the client is rejected.  See below for an
                       extension to accept a client view-only.

                       ...

-afteraccept string    As -accept, except to run a user supplied command after
                       a client has been accepted and authenticated. RFB_MODE
                       will be set to "afteraccept" and the other RFB_*
                       variables are as in -accept.  Unlike -accept, the
                       command return code is not interpreted by x11vnc.
                       Example: -afteraccept 'killall xlock &'
-gone string           As -accept, except to run a user supplied command when
                       a client goes away (disconnects).  RFB_MODE will be
                       set to "gone" and the other RFB_* variables are as
                       in -accept.  The "popup" actions apply as well.
                       Unlike -accept, the command return code is not
                       interpreted by x11vnc.  Example: -gone 'xlock &'

```
you basically set 'string' to the command or shell script you want to run.

The x11vnc FAQ also contains some usage examples and demo scripts:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-accept-opt](http://www.karlrunge.com/x11vnc/faq.html#faq-accept-opt)[/INDENT]

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-gone-lock](http://www.karlrunge.com/x11vnc/faq.html#faq-gone-lock)[/INDENT]

[INDENT][http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-accept](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-accept)[/INDENT]

---

### Post by DexterLB on 2009-07-03
Thank you.

---

