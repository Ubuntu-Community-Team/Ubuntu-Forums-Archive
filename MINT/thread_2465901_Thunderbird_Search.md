---
title: "Thunderbird Search"
date: 2021-08-14
forum: MINT
---

### Post by michaelmacho on 2021-08-14
Hi Everyone

I am new to Thunderbird and Mint Linux as my daily driver.  After many issues with Outlook and Windows I decided to make the shift to Linux and Thunderbird.  I really appreciate everyone's help in getting this working.  

In the past with outlook, I am able to sort the INBOX using the FROM person filed and click on a message and type using the keyboard letters that correspond to the persons name and it would then go directly to a list of emails from that person.  IE:  

Tim Smith 
Tim Smith 
Tim Smith 

Keyboard Strokes Entered:  Tim

It would then go to all of the emails from Tim Smith that are located in the INBOX.   

This was an easy way to find emails from people that said.  Did you get this email.   Or I sent you an email can you help me etc.

I have tried this many times and does not seem to work.  I have also downloaded many search add ins that looked like it might work and have yet to be able to get this functionality working.

**If anyone knows how i can get this to work or has a similar work around please let me know.**

Thank you 
Michael

---

### Post by T6&amp;sfpER35% on 2021-08-14
i don't use thunderbird so can't help there ,don't know how it search work but i can imagine the mainstream linux email client would have that sorted.
anyway ,i use mailspring ,and don't have any troubles searching / finding emails.
just a thought, might want to look into it . or not .

---

### Post by michaelmacho on 2021-08-14
Thank you -  I looked into Mindspring and it does not support Microsoft Exchange.  do you know if there is an add on or way for it to support Exchange accounts.

---

### Post by TheFu on 2021-08-14
I use thunderbird.  It has Quick Filters and a Full deep search.

**Quick filters:** Show the FROM entry if it isn't already in the message list. There is a customize button for that view.  Click on the header button, FROM, in this case to sort ascending or descending, then click the "quick filter" button and begin typing.  That doesn't search just FROM, but all the major fields.

**Deeper Search: **If that isn't sufficient, you can press "<c><s>-F" which will bring up the "Find" search box 
Anywhere there is a down-carrot "V", that's a selection menu. By default, the first search will have "Subject" ----> change that to FROM, leave the "contains" alone and type in the empty text entry. 
[ATTACH=CONFIG]288973[/ATTACH]

At the very top of the Search Messages window, there's a "Search for messages in:" choice/selector.  Local Folders is 100% client-side searching.  If you are connecting to an imap server, then let the server do the searching - it will be much faster.  I run an IMAP server for a number of reasons, but one is so the server can index and search the years and years of messages.

**Other Search Tools: **If you only have local messages, there are other search tools like **Recoll**, which are like having a local google just for your machine. Recoll does soundex searches, so it finds things that aren't exact matches for the query in addition to the things that are.  In understands the different extensions and will show other words in the root-word family.  The downside to Recoll is that indexing is necessary. The search DB isn't live, but only has data from the last time the index was run.
Recoll isn't just for email, but for all files on your system.

Because you asked about email, I'll just list **locate** and **find** as other tools. They won't find emails, but they will find files on the box if you know part of the filename. Locate needs an index.  

Find searches the file system and is an amazing tool, but not so easy to use.  Searching by partial name, date modified, permissions, owner, group, file size, creation date, and a few other file metadata items is possible. But is is a file system scan, which can take time.

---

### Post by TheFu on 2021-08-14
> **michaelmacho said:**
> Thank you -  I looked into Mindspring and it does not support Microsoft Exchange.  do you know if there is an add on or way for it to support Exchange accounts.

All email clients follow standards.
All email servers follow standards.
Any client can be used with any server, IME.  Just look at the standards provided in the server-support-pages, and enter those into the client-connection pages.

MS-Outlook, the client-side email client, connects to any email server that supports standards.  Those tend to be POP3S or IMAPS.  There are standards for receiving emails and for sending emails. 
Thunderbird supports those same standards.

Typically, sending email uses port 587/tcp and starttls for end-user clients to send email using the SMTPS protocol through a specific, authenticated, email server.
Receiving email uses port 993/tcp for IMAPS to receive.  The server for sending and the server for receiving can be the same or different physical machines.

Any email server that doesn't support those standards is broke.  Call the support line and get the connection information for SMTPS and IMAPS. Most ISPs have email connection pages with this information. Mindspring is an ISP.  [https://getmailspring.com/setup/access-mindspring-com-via-imap-smtp](https://getmailspring.com/setup/access-mindspring-com-via-imap-smtp) is theirs.  Using IMAP on port 143/tcp is a security failure, IMHO.

Email clients can point at different servers with multiple accounts and different connection settings for each.

If you seek a more bloated email client to use on Linux, similar to MS-Outlook, there is Evolution.  Last time I used email on Windows, there were 2 programs that were so bloated more RAM had to be bought.  MS-Outlook was one and iTunes was the other.

Thunderbird can do most things that MS-Outlook does, but it has a different philosophy, so things aren't exactly the same.

Gmail supports both IMAPS and authenticated SMTPS for receiving and sending email, but they push really hard for people to use a browser, not a full email client. That's because they can slurp more data from a browser than they can from an email client, but they will also claim that full email clients are less secure. Perhaps, in the google world, that is true. In the rest of the world, where we firewall repeated, failed, email login attempts and can lock down where those attempts are allowed from, I strongly disagree.

---

### Post by coffeecat on 2021-08-14
*Thread moved to **Mint** sub-forum.*

---

### Post by michaelmacho on 2021-08-14
Thank you 
I do not want to use outlook.  Exchange has very specific protacalls and the email client has to support them.  IMAP and POP while supported by exchange is not open on the server and so you need to have a email client that works with "Exchange"  normally most 3rd party email client apps have a plugin and reference support for Exchange.  
In fact I believe on Mindsprings web site it says it does not support Exchange.

Thank you I will try this and advise.

---

### Post by TheFu on 2021-08-14
> **michaelmacho said:**
> Thank you 
I do not want to use outlook.  Exchange has very specific protacalls and the email client has to support them.  IMAP and POP while supported by exchange is not open on the server and so you need to have a email client that works with "Exchange"  normally most 3rd party email client apps have a plugin and reference support for Exchange.  
In fact I believe on Mindsprings web site it says it does not support Exchange.

Microsoft has a long history of breaking standards and using proprietary protocols.  Their email server is broken if they don't follow standards.  Period.

---

### Post by michaelmacho on 2021-08-14
[COLOR=#000000]Microsoft has a long history of breaking standards and using proprietary protocols. Their email server is broken if they don't follow standards. Period.

yes they do and it is very frustrating.  This is one reason i changed over to Linux for my Daily Driver.  I am now just trying to figure a number of things out.  The [/COLOR]

TheFu - 
Thank you -  These are some good work around to what i was originally asking.  For some reason I do not see the search screen you are talking about.  I attached an image of what i think you are talking about in order to get the screen shot you attached.  
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288979&stc=1[/IMG]

i was able to search Chris and it then would display all the emails for Chris etc.

Also I am attaching another screen shot with hopes that I can better explain what I am trying to do.  In the below image as you can see it is sorted using FROM and I would like to highlight one of the emails.  Then type Goo or UDM and it would automatically advance to the Google emails or UDM emails.  Make sense?  I know I was able to do this in my previous email client so i thought i would ask if there is a way to do this in Thunderbird or use an add on of some sort that would then allow this sort of functionality.   
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288980&stc=1[/IMG]

---

### Post by TheFu on 2021-08-14
In your first image, do you see the right side where it says "Filter messages by:...."  deselect all but the Sender. enter "goo" and only the from with "goo" inside will show up in the list. Press 'n' to move to the next unread message.  There are lots and lots of *quick keys* in most programs, including thunderbird.  Over time, they become muscle memory, so I couldn't tell you what each is ... there must be a page somewhere with all of them listed by the current view.  I use n, p, m all the time.

Moving on ... did you see the image I attached above with the Find window?
press "<ctl><shft>-F" which will bring up the "Find" search box. That's the more powerful search for TB. Dbl-clicking a message there opens a new window with just that message.  That can be handy if you want to process lots of similar messages back to back.

Probably nothing you haven't considered already, but maybe not. Some other email handling ideas follow.
For me, all email clients see the same view on the server - thunderbird, nextcloud, K9-Mail, Claws, mutt, or any tool I use on android.  All inbound messages get tagged/filtered.  Thunderbird can use filters that see different parts of the message, then move the message to a different folder. That folder can be local or on the IMAP server.  I don't to client-side filters or tagging, but most people don't run a powerful email server like I do.

Because I use 5+ different email clients/machines daily.  I'd go nuts if I had to see a message that was already handled twice. Once handled, it is done and either deleted or moved to an archive folder. The client used doesn't matter.

For Junk management, anything that looks like junk either to the email gateway, email server, or any active client, gets moved to a spam folder on the server before I ever see it.  Some junk is deleted immediately - like anything with "bitcoin" in it.  Thunderbird can be trained to recognize junk automatically. With a few hundred junk emails, the recognition isn't too bad.

Have you looked at the email filter capabilities built into Thunderbird? If all you have is client-side filtering/organization, then it isn't too bad. Select a message, then in the Message menu choose *Create Filter from message* ... automation is good.  I didn't see an accel key-chord to show that window.

---

### Post by michaelmacho on 2021-08-15
[COLOR=#000000]Have you looked at the email filter capabilities built into Thunderbird? If all you have is client-side filtering/organization, then it isn't too bad. Select a message, then in the Message menu choose [/COLOR]*Create Filter from message ... automation is good. I didn't see an accel key-chord to show that window.*
Oh thank you again 

I have not looked into the email filter capabilities of Thunderbird.  Is this an add on ? or built in and where is it?  I currently use a paid filter SPAM service form APP River and a product called Sane Mail, which is a AI ML product that filters all in bound mail based on a number of parameters. I wonder if it would be smart to run mail through APP River, Sane Mail as it does now and then add the Thunderbird part.  I get over 500 emails a day and it drives me crazy.  Each day after email is read I mark mail into a category which is like the current Thunderbird TAG feature and then the mail automatically goes into one of my SANE Boxes and if not it goes into SANE archive so that by the end of the day I have a 0 Inbox. I have to say one of the most irritating issues i have had is the indexing of email and searching aspect of outlook, it is really bad, as we have an ON PREMM Exchange Server.  Thunderbird seems to be much better, but it is very possible that once i load in all my email accounts it will be about the same in performance of being sluggish and not indexed well etc.  

This is one reason I moved to Linux and Thunderbird in hopes that a much lighter weight OS and email client would help.  I also upgraded the memory from 8 GB to 16 GB and got a larger and much faster SSD drive to which i loaded MINT Linux and Thunderbird.   

On our corporate exchange server that houses 5 email addresses for me for work.  I have only imported the 1 email address to test and get things going, once that is done i will move in and setup the additional 4 email addresses. 

Reg:  [COLOR=#000000]thunderbird, nextcloud, K9-Mail, Claws, mutt, 
[/COLOR]

Do you use all of these email clients to separate your email accounts or do you have them all in 1 account on Thunderbird with the Thunderbird filtering ... you seem to like the filtering a lot.  Why and what makes it so good. 

You may have seen some of my other forum posts about WINE etc.  I am using Word and Excel and PowerPoint as i have used them for over 30 years and the Open Office products are great but not the same to what i am used to as a daily driver.  that being said i am happy that i ditched outlook as it really was a pain and did not work well.  For sure not a light weight email client. 

I look forward to your response, thank you again for your time.

One more thing i forgot to mention in my previous post

Is there a way to change the default search values when i press CTL+Shift and F  -  The default values that I have now are attached in the image.[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288981&stc=1[/IMG]

As you can see the defaults are Subject and Contains ... it would be better for me to have FROM and begins with  or if it captures the FROM in the header of the message perhaps message and Contains.

---

### Post by TheFu on 2021-08-15
BTW, please don't inline images. Some of us pay for connections by the byte and it costs money.  Attachments. Please.  No huge images inline.  Example in post #4.

I have hundreds of email aliases, but only a few accounts - perhaps 20.
I use different client programs because they make sense for different purposes. No single tool works on every platform.  All of them support accessing all the accounts, though I don't have them all connected to all the accounts. Most have my 5 main accounts.

The trick with Outlook has always been to keep the PST file small and create a new one at least yearly.  This feeds into records retention policies and makes deleting records that shouldn't be retained much easier.  I worked in a govt regulated industry with lots of mandatory retention periods and lots of lawsuits. The company had a policy for how long every type of record could and should be retained. 

As for filtering - there are multiple types.  Blocking and organizing. I use both.  Anyone getting over 100 emails a day needs to automate as much as possible or you'll never get off the hamster wheel.  I try to have my inboxes empty daily.

---

### Post by mIk3_08 on 2021-08-15
> **TheFu said:**
> Microsoft has a long history of breaking standards and using proprietary protocols.  Their email server is broken if they don't follow standards.  Period.
hahahahahahaha... agree agree agree and Amen.... :-D  stupefy! Good shot! TheFu. Its actually a boom! 
I just don't know what to say but you are right. Sad to say but you are exactly right. As Steve Jobs says:  Beware of the pirates.

---

### Post by T6&amp;sfpER35% on 2021-12-20
i used mailspring before and then tried thunderbird for a few months , all was good and well until today when i wanted to search a specific email from a sender i know the name off.
the search results (few 100s) from TB is well , just confusing and messy , in my opinion.
right then and there i installed mailspring again,set up my accounts , typed in the sender in search emails, 30 sec later found the email...
for me everything in mailspring is just cleaner and more organized 
i dont want to filter this and filter that to find an email, i want to put in the sender's name in search and that's that.

---

