---
title: "Mail.app or Thunderbird?"
date: 2008-09-23
forum: Mac OSX
---

### Post by Glenn Jones on 2008-09-23
Hi 

I was thinking of migrating from apple's Mail.app to Thunderbird and I was wondering if people know if there are any performance improvemets in doing so. Or in other words which is the best desktop mail application for the mac?

I run osX Tiger if that helps 

Cheers

---

### Post by aysiu on 2008-09-23
You won't see any performance improvements. In fact, my wife switched from Thunderbird to Mail, because Thunderbird keep crashing or hanging. It's possible that the newest version of Thunderbird has better stability than the older versions, but Mail is pretty solid. The other great thing about Mail is the universal inbox you can use (Thunderbird does not have this feature, even with extensions).

That said, I like Thunderbird, because you can junk stuff with one keystroke instead of two. It also generally gives you more control over how folders behave and which ones show up.

---

### Post by explorer59 on 2008-09-23
I have been using both concurrently on a variety of g3 and g4 computers for a couyple of years with both Tiger and Leopard. TBird has always been stable for me. As to which is best, it's a matter of taste and needed features, although I find that I generally prefer Mail. For me, the TBird feature I'd like in Mail is the ability to automatically DL images for specified addresses (or domains).

---

### Post by cyberdork33 on 2008-09-23
I used Thunderbird for a long time and all it did was have issues. I am using Apple Mail now and it works fine.

---

### Post by mips on 2008-09-24
What mail format does Mail use?

I have come to the conclusion that I do not like the Unix mbox format that TB uses. Corruption is unrecoverable as far as I can tell.

---

### Post by Glenn Jones on 2008-09-24
Thanks guys.

The reason for my possible migration from Mail to TBird was so that I could easily sync my laptop and desktop eemail mailboxes with my dropbox account. I did manage to write a script which used rsync between dropbox and mailboxes and vice versa to sync desktop and laptop but there was no way I know of getting it to run on open/close of mail. I thought TBird may have options to run scripts at start/close?

Another option is mobile.me or .mac accouts. DO any of you have any experience with them and is it worth it?

---

### Post by cyberdork33 on 2008-09-24
> **Glenn Jones said:**
> Thanks guys.

The reason for my possible migration from Mail to TBird was so that I could easily sync my laptop and desktop eemail mailboxes with my dropbox account. I did manage to write a script which used rsync between dropbox and mailboxes and vice versa to sync desktop and laptop but there was no way I know of getting it to run on open/close of mail. I thought TBird may have options to run scripts at start/close?

Another option is mobile.me or .mac accouts. DO any of you have any experience with them and is it worth it?
gmail IMAP.

---

### Post by Glenn Jones on 2008-09-24
How would that work?

Would I create directories in my gmail account so I can drop any work emails?

---

### Post by AlphaMack on 2008-09-25
> **mips said:**
> What mail format does Mail use?


emlx, a proprietary format from Apple.

---

### Post by roost3r on 2008-09-27
As has been stated, there is no "real world" performance differences, only "perceived" performance differences. I am surprised that some posters have had ongoing issues with ThunderBird. Since I switched to it a few years ago (it was version 1.5 then), I have had very littel problems with.

As for the mailbox format, I prefer the format ThunderBird uses. A single text file that I can edit if I **had** to.

I am not sure when, and it could have been since version 1, but you can have ThunderBird always load images for addresses in your address book.

If you want to have mailboxes sync'd, ditch POP and move to IMAP. I did this myself just before I switched to ThunderBird. Best thing I ever did for my e-mail since originally choosing to use NetScape back in 1998 (though I switched to Eudora a year later at the request of my employer at the time - was a huge fan of Eudora until I began working in all three of the major OS's all day, then I had to have unity - ThunderBird to the rescue!).

If anyone is having issues with stability in ThunderBird, back up your profile, trash your current installation including the profile storage and then re-install fressh and move mailboxes over one at a time. Often an extension/add-on/plugin can cause the XUL to behave oddly or even crash/hang on you.

---

### Post by mips on 2008-09-27
> **roost3r said:**
> A single text file that I can edit if I **had** to.

Ever try that with a corrupted 800MB mbox file? I gave up and that was after splitting it into smaller files.

Is there no utility out there that will strip out or repair the corrupted sections so I can have a working file again? I have not found one yet.

No it's not my mail, it's a friends and it is the backup.

---

### Post by Glenn Jones on 2008-09-30
As roost3r said one of the resons for moving over to Thunderbird is to use the standard .mbox file format as opposed to apples emlx. If I decide to move away from an apple then at least I can still read my archived emails.

I have had a look at moving from POP to IMAP but unfortunatley the university storage capacity is pathetic and I haven't got sufficient privelages to create any mailboxes on their IMAP server.

I have had a look at unison to sync my file. Has anyone had any experience with it?

Cheers

---

### Post by jrothwell97 on 2008-09-30
In response to the OP, I prefer Mail.app because I find it to be cleaner, a bit faster, and better integrated into the OS than Thunderbird.

That said, I use Thunderbird on my Ubuntu machine, because Evolution is far too bloated.

---

### Post by Erunno on 2008-10-01
When using Thunderbird instead of Mail.app you'll have to do without a lot of Mail's system integration like the address book, keychain, Spotlight, spell checking and other functions. Plus, Thunderbird is not a Cocoa app and has a different control scheme. I'd rather look for an email provider which offers free IMAP (e.g. GMail) than having to endure Thunderbird on a day to day basis in Mac OS X for the remote possibility that I might have to restore my inboxes.

---

### Post by mips on 2008-10-02
> **erunno said:**
> **i'd rather look for an email provider which offers free imap** (e.g. Gmail) than having to endure thunderbird on a day to day basis in mac os x for the remote possibility that i might have to restore my inboxes.

+1

---

### Post by amitai on 2008-10-05
> **Erunno said:**
> When using Thunderbird instead of Mail.app you'll have to do without a lot of Mail's system integration like the address book, keychain, Spotlight, spell checking and other functions. Plus, Thunderbird is not a Cocoa app and has a different control scheme. I'd rather look for an email provider which offers free IMAP (e.g. GMail) than having to endure Thunderbird on a day to day basis in Mac OS X for the remote possibility that I might have to restore my inboxes.

I was going to point out the same thing.  Switching to Thunderbird, you will lose the advantage of Mac OS X Services.

---

