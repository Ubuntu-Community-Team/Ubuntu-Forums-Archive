---
title: "Songbird Last.fm says I need to sub."
date: 2009-08-10
forum: Multimedia Software
---

### Post by Wiebelhaus on 2009-08-10
I understand that this is not  a Songbird support forum , I'm just fishing for anyone that may have ran into this as I'm not finding the issue over at get satisfaction.

Thanks.

As you can see in the screenie , I'm logged in and I do reside in the USA.



[B][I]**Thanks to those who replied , it was a bit hard to find for some reason , but the answer is at [post 6]("http://ubuntuforums.org/showpost.php?p=7771303&postcount=6") and makes perfect sense , I'm not mad at them! And actually the strategy worked because I decided to sub.

Cheers![/I][/B]

---

### Post by starcraft.man on 2009-08-10
Two quick diagnoses. 

1) Can ya log in to lastFM site and play without trouble from this account? If so, not an IP problem.

2) Close songbird, we're going to rule out or expose config problem. Can ya go to your home folder and show hidden files (Ctrl H or .) then find the .songbird config folder. Copy it to another folder like the Desktop. Then delete your configuration for songbird in your home folder. Open songbird and it will generate a new profile, include last.fm as a plugin and try and get lastFM to play. If it works, it's a configuration problem with the profile. If not, my knowledge at an end, I'm not a last user nor can I get it since they shaft Canada like most companies.....

You can always put back the config for songbird and restore everything, close songbird before removal or restoration. Alternatively, this diagnoses can be done with an alternative user account if its quicker/preferred.

Pop into BT IRC if ya want more help. Sure someone is a last user there.

---

### Post by Wiebelhaus on 2009-08-11
> **starcraft.man said:**
> Two quick diagnoses. 

1) Can ya log in to lastFM site and play without trouble from this account? If so, not an IP problem.

2) Close songbird, we're going to rule out or expose config problem. Can ya go to your home folder and show hidden files (Ctrl H or .) then find the .songbird config folder. Copy it to another folder like the Desktop. Then delete your configuration for songbird in your home folder. Open songbird and it will generate a new profile, include last.fm as a plugin and try and get lastFM to play. If it works, it's a configuration problem with the profile. If not, my knowledge at an end, I'm not a last user nor can I get it since they shaft Canada like most companies.....

You can always put back the config for songbird and restore everything, close songbird before removal or restoration. Alternatively, this diagnoses can be done with an alternative user account if its quicker/preferred.

Pop into BT IRC if ya want more help. Sure someone is a last user there.

Thanks for the suggestions bud , Yes , I can use Last.fm without issue and I can also scrobble from songbird with the built in function at the bottom right.

I have removed the profile and recreated and still have the same issue.

---

### Post by krul on 2009-08-11
I also get this, but I am not a paying last.fm subscriber....I assume you are??

---

### Post by Wiebelhaus on 2009-08-11
> **krul said:**
> I also get this, but I am not a paying last.fm subscriber....I assume you are??

I'm in the USA , it's free here.

---

### Post by Wiebelhaus on 2009-08-11
[From:]("http://getsatisfaction.com/songbird/topics/in_order_to_listen_to_last_fm_radio_you_must_be_a_subscriber")

[Michael Purses]("http://getsatisfaction.com/people/mpurses")

> This is due to Last.fm's changes in their [Radio API]("http://www.last.fm/api/radio") - allowing to only stream radio to paid subscribers.

They announced back in March that they were going to make changes to their Radio API/Subscription Services:
[http://blog.last.fm/2009/03/24/lastfm...]("http://blog.last.fm/2009/03/24/lastfm-radio-announcement")
[http://blog.last.fm/2009/03/30/radio-...]("http://blog.last.fm/2009/03/30/radio-announcement-revisited")
[http://blog.last.fm/2009/04/22/radio-...]("http://blog.last.fm/2009/04/22/radio-subscriptions")
And by reading them, it could confuse users. It doesn't effect people inside the USA, UK, and Germany. [COLOR="Red"]***But that is for their "ad-supported Web"***[/COLOR] and [Official Client]("http://www.last.fm/download").

What they also announced among those blog posts were changes to their radio API:
[The Future of Last.fm Radio APIs.]("http://www.last.fm/group/Last.fm+Web+Services/forum/21604/_/517212")
And external apps (third parties) are not allowed to stream radio to non-subscribers now.

You can also find the official SB bugs here:
[Bug #16403]("http://bugzilla.songbirdnest.com/show_bug.cgi?id=16403")
[Bug #16404]("http://bugzilla.songbirdnest.com/show_bug.cgi?id=16404")

---

