---
title: "Logging connection attemp to my svn server"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by hexanol on 2009-05-20
Hi,

here's the situation: I'm hosting a couple of small private SVN repository on one of my computers. I'm using the custom SVN protocol, i.e. the repositories are accessible via a svnserve process. svnserve doesn't have any logging capabilities, so currently, everyone on the Internet is free to do brute-force attack on my server, by repeatedly trying different username/password combination, without being discovered. This is certainly not something I appreciate a lot, and I would like to correct this situation.

Currently I don't have much the time to look for complex IDS/IPS setup, or anything that would take me a couple of hours to understand and configure. I'm looking for a solution that would let me, at least, to see who had try to connect to the svnserve process (on TCP port 3690). I though about running tcpdump and capturing only packet with TCP port destination 3690, but I find this solution rather inflexible. Anyone has suggestion ?

---

### Post by hexanol on 2009-05-22
Any ideas, someone ?

---

