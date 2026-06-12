---
title: "Democracy Player"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by jlh on 2006-12-02
I have downloaded and installed Democracy Player 9.2.1 beta on Dapper.  I have two, maybe three problems.

1.  I can only launch Democracy as root.  If I launch as user or sudo, I get this message:

INTERNAL ERROR on Browser End: JavaPluginFactory5 init - no agent?

System error?:: No such file or directory

I encountered this in installation.  However, I located and installed the JRE5 update.  Inasmuch as I can launch as root, I seem to have a permissions problem somewhere.  I don't find it in the Java installation, however, where I am permissioned to execute as user.  I don't know how to go about troubleshooting this.

2.  Ok, so I've launched as root, and selected a feed.  The feed downloads.  Virtually always, however, the Democracy just crashes.  I have to start over.

3.  Infrequently, I've launched the video.  I'm not sure that I have sound, however.  I've not launched enough videos yet, however, to determine if this is a problem.  Too many crashes thus far.

---

### Post by pestilence4hr on 2006-12-02
I wonder if you would have better luck with the SVN version of democracy...I got it going in about 10 minutes on my laptop.  Instructions can be found here:
[https://develop.participatoryculture.org/democracy/wiki/GTKX11BuildDocs](https://develop.participatoryculture.org/democracy/wiki/GTKX11BuildDocs)

---

### Post by pestilence4hr on 2006-12-02
One more thing, I don't think any flash-based videos will have sound.  Democracy uses xine, which has a bug in flv play.  Too bad, they work fine in mplayer.

---

