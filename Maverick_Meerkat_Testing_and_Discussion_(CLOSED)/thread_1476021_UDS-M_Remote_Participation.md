---
title: "UDS-M Remote Participation"
date: 2010-05-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Technoviking on 2010-05-07
(*Upto date information at [https://wiki.ubuntu.com/UDS-M/RemoteParticipation](https://wiki.ubuntu.com/UDS-M/RemoteParticipation)*)

[COLOR="Red"]**UDS-M is held in Belgium, timezone of which will be UTC+2 (CEST)**[/COLOR].

**Schedule**
[http://summit.ubuntu.com/uds-m/](http://summit.ubuntu.com/uds-m/)

**Internet Relay Chat**
[LIST]
[*]All channels are hosted on [irc.ubuntu.com]("https://help.ubuntu.com/community/InternetRelayChat")
[*]Overall discussion, including plenary: #ubuntu-uds on freenode.
[*]Discussion Channels - The tracks are shuffled around different rooms, so the IRC channels are per room, not per track. Here are the channels, which corresponds to the room of the session in the schedule.
[/LIST]

[LIST]
[*][#ubuntu-uds-auditorium-canopee]("http://webchat.freenode.net/?channels=ubuntu-uds-auditorium-canopee")
[*][#ubuntu-uds-amarente]("http://webchat.freenode.net/?channels=ubuntu-uds-amarente")
[*][#ubuntu-uds-bois-dentelle]("http://webchat.freenode.net/?channels=ubuntu-uds-bois-dentelle")
[*][#ubuntu-uds-cocobolo-1]("http://webchat.freenode.net/?channels=ubuntu-uds-cocobolo-1")
[*][#ubuntu-uds-cocobolo-2]("http://webchat.freenode.net/?channels=ubuntu-uds-cocobolo-2")
[*][#ubuntu-uds-cocobolo-3]("http://webchat.freenode.net/?channels=ubuntu-uds-cocobolo-3")
[*][#ubuntu-uds-delfino]("http://webchat.freenode.net/?channels=ubuntu-uds-delfino")
[*][#ubuntu-uds-ebene]("http://webchat.freenode.net/?channels=ubuntu-uds-ebene")
[*][#ubuntu-uds-flamboyant]("http://webchat.freenode.net/?channels=ubuntu-uds-flameboyant")
[*][#ubuntu-uds-ginko]("http://webchat.freenode.net/?channels=ubuntu-uds-ginko")
[*][#ubuntu-uds-jatoba]("http://webchat.freenode.net/?channels=ubuntu-uds-jatoba")
[*][#ubuntu-uds-kawi]("http://webchat.freenode.net/?channels=ubuntu-uds-kawi")
[*][#ubuntu-uds-mohogany]("http://webchat.freenode.net/?channels=ubuntu-uds-mohogany")
[*][#ubuntu-uds-mangrove-3]("http://webchat.freenode.net/?channels=ubuntu-uds-mangrove-3")
[*][#ubuntu-uds-mangrove-4]("http://webchat.freenode.net/?channels=ubuntu-uds-mangrove-4")
[*][#ubuntu-uds-palissandre]("http://webchat.freenode.net/?channels=ubuntu-uds-palissandre")
[*][#ubuntu-uds-rosewood]("http://webchat.freenode.net/?channels=ubuntu-uds-rosewood")
[*][#ubuntu-uds-snakewood]("http://webchat.freenode.net/?channels=ubuntu-uds-snakewood")
[*][#ubuntu-uds-teck]("http://webchat.freenode.net/?channels=ubuntu-uds-teck")
[/LIST]

You can find logs from Monday afternoon onwards at: [http://ubottu.com/uds-logs/](http://ubottu.com/uds-logs/)

**Icecast**
[http://icecast.ubuntu.com/](http://icecast.ubuntu.com/)
Unfortunately there is no live stream for the plenary sessions.

**Recording a Live Stream**
Use mplayer to capture the livestream (e.g for room3):

```
mplayer -playlist http://icecast.ubuntu.com:8000/room3.ogg.m3u -ao pcm:file=/tmp/mystream.wav -vc dummy -vo null
```
and use lame for encoding as .mp3:

```
lame -m s /tmp/mystream.wav -o "/tmp/uds_room3.mp3"
```
for scheduling you can use cron to start mplayer and pkill to stop the recording.

**Gobby**
[LIST]
[*]gobby.ubuntu.com
[*]Gobby is being used at UDS to collaborate on the specifications that are being written and to facilitate remote participation.
[/LIST]
To take part, please install Gobby (available in universe) and tell it to connect to gobby.ubuntu.com. You will be presented with a list of documents being edited. During any session or meeting, and particularly at the end of one, please do make a local backup of your documents. WARNING: There is a new gobby in karmic, gobby-infinote, we will NOT be using this at UDS since we need for people on older releases to participate. Ensure you are using the "gobby" package.

**Lifestream**
A stream of all Ubuntu and UDS posts made to Identi.ca, Twitter, and Flickr can be found at [http://summit.ubuntu.com/media/lifestream.html](http://summit.ubuntu.com/media/lifestream.html)

**Videos**
We will be recording certain sessions and all the plenary sessions at UDS. You can follow along with the videos as we post them on the Ubuntu community on Miro. If you want to automatically receive updates when videos are available we recommend that you install Miro and click on the miro links at the site to subscribe to the video feeds. These videos will be in Ogg Theora format and is the recommended method for watching UDS videos.

[http://ubuntu.mirocommunity.com/](http://ubuntu.mirocommunity.com/)

**Micro-blogging**
Micro-blogging is a form of blogging that allows users to send brief text updates of 140 characters or less. It is a great way to inform the Ubuntu community of discussions and news that happen during UDS. Many Ubuntu users get there news from UDS from microblogging sources. During UDS-Mountainview, Identi.ca saw more traffic during UDS than during the night of the U.S. Presidential elections.

Microblogging is not a replacement for gobby or IRC, which have important uses during an UDS event. It should be used as a tool to communicate with other people at UDS and the wider Ubuntu user community.

Suggested ways to use microblogging at UDS:

[LIST]
[*]Announce session topics at the beginning of the session.
[*]Ask for feedback from the community during the session discussion.
[*]Dent/tweet important discussion points during the sessions.
[*]Dent/tweet any news worthy items during UDS (Kernel version, encrypted swap by default, etc...).
[*]To plan social events and gatherings during UDS.
[/LIST]

**Identi.ca**
We encourage people at UDS to create an account on [Identi.ca]("http://identi.ca/"), an open source micro-blogging platform if they don't already have an account. If you have a Twitter account you can link it your Identi.ca account and posts you make to Identi.ca will automatically forwarded to Twitter.

In identi.ca, please use the [!ubuntu]("http://identi.ca/group/ubuntu") and [!UDS]("http://identi.ca/group/uds") groups in your message, which already have many followers. These automatically post to the hashtags #ubuntu and #uds, if you want to follow and are not interested in sending.

**Gwibber**
Gwibber is an open source microblogging client for GNOME developed with Python and GTK. It supports Twitter, Jaiku, Identi.ca, Facebook, Flickr, Digg, and RSS. Gwibber is available in universe in Ubuntu 9.04+.

[https://launchpad.net/gwibber](https://launchpad.net/gwibber)
[https://wiki.ubuntu.com/Gwibber](https://wiki.ubuntu.com/Gwibber)

---

