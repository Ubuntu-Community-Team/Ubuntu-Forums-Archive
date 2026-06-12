---
title: "Odd Dansguardian problem"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by dlefevre on 2009-02-18
I have an odd Dansguardian issue maybe one of you have seen before.  I upgraded my organization's gateway machine last week and with it I brought everything on it up to the latest versions.  After the upgrade I now have at least one machine that shows plain text in Firefox instead of an interpreted HTML page when there is a block.   Like so...

> 
TTP/1.0 200 OK
Content-type: text/html

<html>
<head>
<title>Access Denied</title>
</head>
<body bgcolor=#FFFFFF>
<center>
<table border=0 cellspacing=0 cellpadding=2 height=540 width=700>


In addition, blocked ads also show uninterpreted HTML instead of a block page.

In IE it actually shows the page, but with the headers ("TTP/1.0 200 OK.." without the starting "H") showing at the top, probably because IE is set up to just interpret the HTML anyway even though it's coming through in plain text.

I am not exactly sure what to even troubleshoot on this.  It's happening on only one machine (so far) but it did not do this on the previous version of dansguardian, though I realize since it's on one machine it's probably related to the setup of that machine.  Obviously the "HTTP/1.0 200 OK" header isn't getting interpreted correctly on that machine.  Anyone got any ideas on what I should look for on either the dansguardian setup side or on the individual machine?

---

