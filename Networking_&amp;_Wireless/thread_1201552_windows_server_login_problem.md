---
title: "windows server login problem"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by miroslav_karpis on 2009-07-01
Dear Friends,

please can you help me with following problem?

I have one PC(linux) and one server(windows). On that server on one port we have a SVN repository. In Places->Network I can see the server.

When I go via:
- firefox (enter svn address for example [http://myServer:81/svn/codeOne](http://myServer:81/svn/codeOne) I got 'address not found'
- rapidSVN I got: Error: Error while performing action: OPTIONS of 'http://myServer:81/svn/codeOne': Could not resolve hostname `myServer': Host not found ([http://myServer:81](http://myServer:81))

Strange is, that on another computer(linux - same version) everything runs correctly. 

Any suggestions pls.??

---

### Post by Boondoklife on 2009-07-01
have you tried going to it by ip instead of hostname?

---

### Post by wojox on 2009-07-01
Try

```
http://svn.myServer:81/svn/codeOne
```

---

### Post by miroslav_karpis on 2009-07-02
> **maletek said:**
> have you tried going to it by ip instead of hostname?

this helped - thanks a lot!!!

---

