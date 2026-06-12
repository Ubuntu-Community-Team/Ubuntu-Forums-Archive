---
title: "How Do I Submit or Edit Freedb CD Info?"
date: 2011-01-18
forum: Multimedia Software
---

### Post by clevertomato on 2011-01-18
I have searched the web and these forums and have come up empty-handed. There must be a way... even and easy way... to submit or edit freedb information for a CD. Grip supposedly had the ability but 1) it seems to be no longer maintained and 2) it seems it requires sendmail to be installed. I've read that submissions can be made by email, but 1) I've found no information on how to do this (ie structure and content of email) and 2) that's a lame way to have to do this.

This shouldn't be difficult (much less impossible). What am I missing?

---

### Post by clevertomato on 2011-03-25
bump

---

### Post by lilbill on 2011-05-30
I've done it a few times via email.  The programs cd-discid and cddb-tool are useful for generating the required data.  cddb-tool can be installed from the repos by installing abcde
```
sudo apt-get install abcde cd-discid
```

Then, pop the cd in your cd-rom drive and try
```
cd-discid devname
```
where devname is the name of your cd-rom.  On my machine this is /dev/cdrom.  You should get some output like
```
b20c680c 12 150 20767 32892 47645 68990 87095 107210 119500 137185 160902 186732 205667 3178

```
The first number is the disc id and the others are the track offsets.

You can then pass these to cddb-tool to generate a template freedb file and save it in fname by typing
```
cd-discid devname | xargs cddb-tool template > fname
```
From there you can edit the information needed.  Notice the list of genres in the file, choose one of those to replace the category value.

Finally, you can submit the entry via email.  The addresses to use are [EMAIL="test-submit@freedb.org"]test-submit@freedb.org[/EMAIL] and [EMAIL="freedb-submit@freedb.org"]freedb-submit@freedb.org[/EMAIL].  The former should be used to test your submission.  You will receive a reply describing any errors that it finds.

The subject of the message needs to be "cddb genre disc-id" where genre and disc-id are replaced with the appropriate values for your disc.  The body of the message should contain the text of the edited cddb-tool template file.  Also, if there are any other issues (like the revision number) see the file [http://ftp.freedb.org/pub/freedb/latest/DBFORMAT]("http://ftp.freedb.org/pub/freedb/latest/DBFORMAT") which describes the freedb file format.

I've attached a copy of a recently submitted file to this post for reference.  Good luck!  (I hope someone chimes in with a better method for doing this...maybe I just found a new project ;))

---

### Post by clevertomato on 2011-06-03
@[lilbill]("http://ubuntuforums.org/member.php?u=699352"): Thanks for the detailed reply. It seems prohibitive for someone to mess with all that to contribute to freedb, but I will probably do it for the principle of it.

---

### Post by Danstroem on 2012-02-12
Thanks lilbill,__

that was really helpful!!

---

### Post by ghat on 2012-02-13
[ FreeDB Submit New Entries Document ](http://ftp.freedb.org/pub/freedb/misc/freedb_submit_newentries.zip)

> 
FREEDB SUBMISSION
-----------------

Your software may allow users to enter freedb data and then submit it to the
freedb archives.
There are two methods of submission: via e-mail or via http using submit.cgi
It is up to you, if you support one or both of these methods.


1. Submission via e-mail
------------------------

The method of submission is to send the entry to following address via e-mail:

	[email]freedb-submit@freedb.org[/email]

You may implement a button or somesuch in your software's user-interface to
facilitate this.  The destination e-mail address should be made
user-configurable.  Submissions are silently accepted, and no confirmation
of receipt is sent to the submitter.  Rejected submissions are automatically
returned to the sender via e-mail with an explanation of the reason for the
rejection.

There should be one e-mail message per freedb entry.  The e-mail subject line
should be in the form "cddb category discid".  For example:

Subject: cddb rock 850f970b

You may optionally set an additional "X-Cddbd-Note:" header line, specifying
an arbitrary message to be included at the top of any rejection notice that 
may be sent to the submitting user. You could e.g. add a note about your 
support-address give the user a chance to contact you, if there are problems 
to successfully submit using your program. The length of the arbitrary message 
is limited to 70 chars.

The body of the e-mail message should be in the format of a freedb file entry
as described in the database format specification. The messages should contain
only plain ASCII text. Do not attach encoded information or add special escape
sequences.

The master freedb accepts only submissions in the US-ASCII, ISO-8859-1 and
UTF-8 character sets. If your program supports UTF-8 and protocol level 6,
you should always use UTF-8 for submissions and specify UTF-8 as the charset
of the e-mail, even if the submission contains no 8bit-characters and would 
therefore also be valid as US-ASCII. Only submissions specifying UTF-8 as the
charset in the e-mail headers are allowed to update existing entries that
contain characters, which can not be represented in US-ASCII or ISO-8859-1.

Note that the disc ID specified in the e-mail subject line should also appear
in the list of disc IDs in the DISCID= field of the freedb file entry. If not,
it is considered an error and the submission will be rejected.

You should only allow categories that are currently supported by the freedb.
Valid categories are: blues, classical, country, data, folk, jazz, misc,
newage, reggae, rock and soundtrack 
Submissions specifying unsupported categories will be rejected.

Please do not allow a user to submit CD database entries that have completely
unfilled contents (i.e., blank information in the disc artist/title as well as
the track titles, or filled with useless default information like "track 1",
"track 2", etc.). While the current CD database server checks and rejects
submissions that have a blank DTITLE line, it doesn't (and can't feasibly)
check the track titles effectively, nor can it check any of these fields
if they are filled with a default string.  If it were, it would have to be
hacked to know about the default strings of every possible client.

Thus, please design your client with this in mind. This is a somewhat
tricky thing to do, as some CDs contain blank tracks with no titles
and you need to allow for that.  An example minimum requirement
that a CD player client should meet is listed below:

1. Don't allow the "send" or "submit" feature to be activated if the CD
   database information form is not edited at all.
2. Check that the disc artist/title contains something (that the user
   typed in).
3. Check that the majority of the tracks have a title filled in by the user.
   
This should minimize the amount of useless garbage being submitted
into the CD database.

Before you release your software, please be sure that it produces submissions
that adhere to the freedb file format, and that the frame offset, disc
length, and disc ID information are correctly computed. For testing, please
make your software send submissions to the following e-mail address (rather
than the real submission site at [email]freedb-submit@freedb.org[/email]):

	[email]test-submit@freedb.org[/email]


freedb submissions sent to the test e-mail address will be sanity-checked 
by the freedb server and pass/fail confirmation will be sent back to the 
submitter, but the submission will not actually be deposited in the CD 
database. Please do _not_ send submissions in "submit" mode until you have 
tested your program with several different CD's.

When you feel your application is ready to support submissions, we would 
appreciate, if you would contact us and provide a copy of your program 
before releasing it, so we can check if everything is really OK.


2. Submission via http
----------------------

The method of submitting via http is, to transmit the entry to the database
through a CGI program, which is present at the same location as the cddb.cgi.
The standard address for this is:

[http://freedb_server/~cddb/submit.cgi](http://freedb_server/~cddb/submit.cgi)

where freedb_server is the address of the selected freedb-server. 

You may implement a button or somesuch in your software's user interface to
initiate submissions. Rejected submissions are automatically returned via
e-mail to the sender specified in the "User-Email" header field (see below)
with an explanation of the reason for the rejection.

To submit via the cgi-program, you must use the "POST" method of sending data;
"GET" is not supported. Several HTTP "Entity-Header" fields (described below)
must be included in the data followed by a blank line, followed by the
"Entity-Body" (the freedb entry) in the format described in the database-format 
specification.
The header fields are:

Category: valid_freedb_category
Discid: cd_discid
User-Email: username@domain
Submit-Mode: test_or_submit
Content-Length: freedb_entry_length
Charset: character_set_of_freedb_entry (optional)
X-Cddbd-Note: message_for_user         (optional)

Where

- "valid_freedb_category" is a valid freedb category (valid categories are:
  blues, classical, country, data, folk, jazz, misc, newage, reggae, rock,
  soundtrack). Submissions with an invalid category specified will be rejected.

- "cd_discid" is the 8-digit hex CDDB/freedb disc ID of the entry (see 
  Appendix A). This has to be exactly the same disc ID that appears in the
  "DISCID=" section of the entry being submitted. If not, the entry will be
  rejected.

- "username@domain" is the valid e-mail address of the submitting user. This
  is required, as the server must be able to notify the submitter, if the
  submission was rejected. So you should _never_ fill this with a default
  value. Your program should refuse to submit anything, if the user has not
  specified an e-mail-address.

- "test_or_submit" is the word "test" or "submit" (without the surrounding
  quotes), which specifies if the submission is a test submission or a real
  submission to the database (test submissions are described below).

- "freedb_entry_length" is the size in bytes of the freedb entry being
  submitted. This number covers only the "Entity-Body" (without the blank line
  that separates it from the header).

- "character_set_of_freedb_entry" is US-ASCII, ISO-8859-1 or UTF-8 (can be lower
  case). This specifies the character set the submitted entry has been encoded
  in. If your application knows the user's character set, then you should
  specify it here. If your program supports UTF-8 and protocol level 6,
  you should always use UTF-8 for submissions and specify UTF-8 as the charset
  of the e-mail, even if the submission contains no 8bit-characters and would 
  therefore also be valid as US-ASCII. Only submissions specifying UTF-8 as the
  charset in the headers are allowed to update existing entries that contain
  characters, which can not be represented in US-ASCII or ISO-8859-1.
  The default charset value if no charset is specified is ISO-8859-1 for
  backwards compatibility.

- "message_for_user" is an arbitrary message to be included at the top of
  any rejection notice that may be sent to the submitting user. The length of
  the arbitrary message is limited to 70 chars.

To see, how a correct submission should look like, take a look at the following
example:

POST /~cddb/submit.cgi HTTP/1.0
Category: newage
Discid: 4306eb06
User-Email: [email]joe@myhost.home.com[/email]
Submit-Mode: submit
Charset: ISO-8859-1
X-Cddbd-Note: Sent by free CD player - Questions: [email]support@freecdplayer.org[/email].
Content-Length: 960

# xmcd
#
# Track frame offsets:
[ data omitted for brevity ]
PLAYORDER=

Note the blank line between the "Content-Length" header field and "# xmcd"
which marks the beginning of the freedb entry. This complies to the standard 
http header behaviour where the http header information is separated by a 
single newline from the body content. Check [http://www.w3.org/Protocols/](http://www.w3.org/Protocols/)
for more information on the http in general.

The CGI does a quick check on the submitted data (a more thoroughly check of
the entry is made later by the server, which notifies the user by e-mail if the
submission has been rejected) and responds to a submission
with a 3-digit response code followed by a description. 
Currently the following response-codes are used:

200 OK, submission has been sent.
500 Missing required header information.
500 Internal Server Error: [description].
501 Invalid header information [details].

where "details" can be one of the following:
freedb category
disc ID
email address
charset

The body of the freedb submission must be sent exactly as described in 
Appendix B. Do _not_ encode the data in any way before transmitting it; data
must be sent as raw text. Windows programmers should not use the Windows URL
encode function prior to calling the submit CGI program. Doing so may lead to
corrupt data being sent, causing rejected submissions.

Please do not allow a user to submit CD database entries that have completely
unfilled contents (i.e., blank information in the disc artist/title as well as
the track titles, or filled with useless default information like "track 1",
"track 2", etc.). While the current CD database server checks and rejects
submissions that have a blank DTITLE line, it doesn't (and can't feasibly)
check the track titles effectively, nor can it check any of these fields
if they are filled with a default string.  If it were, it would have to be
hacked to know about the default strings of every possible client.

Thus, please design your client with this in mind. This is a somewhat
tricky thing to do, as some CDs contain blank tracks with no titles
and you need to allow for that.  An example minimum requirement
that a CD player client should meet is listed below:

1. Don't allow the "send" or "submit" feature to be activated if the CD
   database information form is not edited at all.
2. Check that the disc artist/title contains something (that the user
   typed in).
3. Check that the majority of the tracks have a title filled in by the user.
   
This should minimize the amount of useless garbage being submitted to the 
CD database.
	
Before you release your software, please be sure that it produces submissions
that adhere to the freedb file format, and that the frame offset, disc
length, and disc ID information are correctly computed.
For testing, please make your software sends submissions with the
"Submit-Mode" HTTP header field set to "test".

freedb submissions sent in test mode will be sanity-checked by the freedb
server and pass/fail confirmation will be sent back to the submitter, but 
the submission will not actually be deposited in the CD database. Please do 
_not_ send submissions in "submit" mode until you have tested your program 
with several different CD's.

When you feel your application is ready to support submissions, we would 
appreciate, if you would contact us and provide a copy of your program 
before releasing it, so we can check if everything is really OK.


---

### Post by ghat on 2012-02-13
Is there a way to submit cd-cover jpegs to freedb ?

---

