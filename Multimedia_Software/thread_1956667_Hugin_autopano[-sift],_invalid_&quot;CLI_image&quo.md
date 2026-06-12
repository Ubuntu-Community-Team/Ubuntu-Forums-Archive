---
title: "Hugin autopano[-sift], invalid &quot;CLI image&quot; problem"
date: 2012-04-11
forum: Multimedia Software
---

### Post by doubi on 2012-04-11
Hi all,

***edit*** Post title should read "CIL image", not "CLI image"

Hugin isn't aligning images automatically for me. I am alerted that the following command fails with exit status 2:
```
autopano-complete --points 20 -o /tmp/foo  "/my/photos/01.jpg" "/my/photos/02.jpg" ... "/my/photos/09.jpg" 
```When run in the terminal, it appears that the keypoints are generated, but the eventual error message relates to another command:
```
Cannot open assembly '/usr/bin/autopano': File does not contain a valid CIL image.
```A little searching revealed that this is a Mono error. I'm (still) running _Ubuntu 10.04 32bit_. My mono version information is:
```
Mono JIT compiler version 2.4.4 (Debian 2.4.4~svn151842-1ubuntu4)
Copyright (C) 2002-2010 Novell, Inc and Contributors. www.mono-project.com
    TLS:           __thread
    GC:            Included Boehm (with typed GC)
    SIGSEGV:       altstack
    Notifications: epoll
    Architecture:  x86
    Disabled:      none

```The `autopano` command doesn't seem to have a version information flag, or specify which version of Mono/CLI is required.

Possibly relatedly, one of the startup tips in Hugin states:
> The Autopano and Autopano-SIFT programs can be used to create control points automatically. Please install one of them if you haven't already done so.I have a **package** called `autopano-sift` and a **command** called `autopano`, but no **package** called `autopano` or **command** called `autopano-sift`.

So my two questions are:

1) Given that my update manager seems satisfied with my current Hugin / autopano-sift / Mono versions, how can I solve this apparent misunderstanding between my installed Mono and the autopano tool?

2) When Hugin talks about "the Autopano and Autopano-SIFT programs", what exactly does it mean? Is there a 'vanilla' autopano package I could install, which would have its own `autopano` program which would solve my issue?

Many thanks!

---

