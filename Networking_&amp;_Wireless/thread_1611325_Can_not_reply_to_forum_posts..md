---
title: "Can not reply to forum posts."
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by ajgreeny on 2010-11-01
I have a very strange problem with ubuntuforums on a netbook running ubuntu 10.10 with Firefox 3.6.12, and fully updated.  It is actually Mint 10, but it is largely the same and I have the same problem with a live USB of ubuntu 10.10 and 10.04.

I can download things with no problem using wireless, which connects easily, and I can access this forum with no difficulty.  However when I try to reply to a post here, I can get the reply window and write a reply but when I hit the submit button, the status bar says either **Connecting to ubuntuforums.org** or **Waiting for ubuntuforums.org**, and it just sits there.  Sometimes a download dialog appears asking if I want to open or save a **newreply.php** file, which having saved is just an empty file.  If I connect by cable I can reply with no problem, it is just wireless that gives this anomaly.

I wondered if it was a FF profile problem, so copied a profile from another laptop also running 10.10 which connects with wireless, but allows me to reply without problem.

Any clues, anybody?  I have searched this forum and found one or two references but no answer.  I am certainly logged in as a member, though I have just noticed that the login info at the top of the page suggests my last login was 7 hours ago, though I know that is not true, it was just minutes ago.

---

### Post by Iowan on 2010-11-01
I have occasionally had problems with cookies getting disabled. Another source of trouble is Javascript.

---

### Post by ajgreeny on 2010-11-02
I have already tried deleting all cookies from this site, and double checked as far as possible that sun-java6-plugin and sun-java6-jre etc etc are all installed and up to date, but so far it makes no difference.

the FF profile I changed to is from another computer running wireless with ubuntu 10.10, and that does not have the problem at all.

I have just swapped from one router to an older router, both Netgear, and both with the same settings, though one is b.g, the newer one b,g,n.  I will see in a second or two when I finish typing here whether ot noit that has changed anything, though I see no good reason why it should.

EDIT:

Well, it is now all working, so something has happened!  I will swap routers back again and see if it gives me the problem still, as the new one does give a slightly stronger signal.

Wish me luck.  I will report back.

---

### Post by ajgreeny on 2010-11-02
Ok, it's the router causing the problem, though why it should be I can not imagine.  Having swapped back to the new one again, I once more can not get the **reply** to post to work, and the browser just sits and goes nowhere.

I shall try to investigate further, and completely start again, resetting  the new router to factory settings so that I can try to get it to work as it should.

However, does anybody have any ideas about what could be wrong or different, making this strange problem appear;  I would be delighted to hear from you.

EDIT:
I have just had a thought, related to this:-
The setup system of the router has a completely automatic setup wizard which I started to use.  I subsequently noticed in all the documentation that for it to work properly Windows XP or later is required, which we don't have any more.  Nevertheless the router seemed to work extremely well, apart from this weird problem.  I hope a factory reset, and then a completely manual setup using the web-browser will put things right.

Once again, I will keep you all posted, just in case it helps other people in the future.

---

### Post by ajgreeny on 2010-11-09
I have at last sorted this problem out, though I admit I don't know for certain what was causing the block on answers.

I have reset the router to factory settings and started again with that, and also did not this time make use of the windows setup wizard at all, but did it all in the web-browswer.

However, most importantly I suspect, I have removed Mint 10, and gone back to ubuntu 10.04 UNE using the gnome desktop.  This has a later edition of sun-java6-plugin, needed for forum replies, I think, and now all is working as it should.

Any thoughts, anybody, on the most likely cause?

Marked as solved, now, so I'm a happy bunny!

---

