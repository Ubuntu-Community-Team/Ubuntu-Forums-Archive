---
title: "How to enter my Netflix info?"
date: 2008-02-23
forum: Mythbuntu
---

### Post by locoHost on 2008-02-23
Running Mythbuntu 7.10

How do I tell Mythbuntu my Netflix account info? I see nothing in the settings.

Thanks! :-)

---

### Post by newlinux on 2008-02-24
I don't use mythflix, but this may help you.

[http://www.mythtv.org/wiki/index.php/MythFlix_README](http://www.mythtv.org/wiki/index.php/MythFlix_README)

It appears you have to do it commandline...

---

### Post by YogiPaolo on 2008-03-07
Hello.

I'm very pleased with Mythtv so far. I have a dedicated MythTV server/backend and I use the frontend on my daily-drive desktop.

I too am having issues configuring MythFlix.

As per the readme, there is a script to run. The readme describes this:
```
  /usr/local/share/mythtv/mythflix/scripts/netflix.pl -L <userid> <passwd>  
```

but I found the script here: 

```
 /usr/share/mythtv/mythflix/scripts/netflix.pl 
```

So, on running: 

```
 /usr/share/mythtv/mythflix/scripts/netflix.pl 
```

I get: 
```
 Status Code: 501 
```

The readme advises:

>  If you run across the following error

LWP::UserAgent::request: Simple response: Not Implemented or a 501 error when running the previous lines, install Crypt::SSLeay

Note: You may also need to install LWP::UserAgent. The easiest way to do this is open CPAN and type install LWP::UserAgent 

I discovered that I do have CPAN on my box (lord knows what package this came with). I have slightly more than zero idea what CPAN is besides its general description. I will RTFM, but I do learn better from being shown something rather than reading FMs. So if someone can suggest the best ways to install the above mentioned packages with CPAN, I'd appreciate it.

If I manage to figure out how to install these packages, I will post the code.

I look forward to the expansion of this thread!

Linux Rules, especially Ubuntu!

---

### Post by jakev383 on 2008-03-08
Installing CPAN modules isn't too hard. First, at the CLI, let get some of the deps:
```
sudo apt-get install build-essential
```
Once that's done, let's get into the perl interface:
```
sudo perl -MCPAN -e shell
```
That will get you into the right spot. It may ask if you are ready for a manual configuration - just say no and let it do the defaults.  The I'd first make sure CPAN is up to date/installed:
```
install Bundle::CPAN
```
Answer yes to any question about prepending modules. When it asks about modifying your config for libnet say no.
Once that's done, install your missing module:
```
install LWP::UserAgent
```
Once again answer yes to any modules that need to be prepended.

That was all from memory, so I may have missed a step or two in there. There's undoubtedly some posts in the general forum about installing CPAN and the likes, or just post any errors here.
Enjoy!

---

### Post by ctucker10 on 2008-08-12
Entering my Netflix info was not as straightforward as it could have been, I managed to do it this way...via the command line.

I went to:

[https://help.ubuntu.com/community/MythFlix](https://help.ubuntu.com/community/MythFlix)

...for general instructions, but they didn't work (for me) verbatim. The first thing I did was to run the following script, substituting my Netflix username (my e-mail address) and password:

$ /usr/share/mythtv/mythflix/scripts/netflix.pl -L <username> <password>

In my case, the script ran without errors. It returned "Code 200" so I moved on.

The Community Docs then instructed me:

"You must now setup some browse-rss feeds in order to spawn mythconverg.netflix (the database):

-Go to Utilities/Setup --> Setup --> Info Center Settings --> Netflix Settings
-Choose at least one of the browse-rss feeds 
-Go to Netflix.com and login. At the very bottom of the page click on "RSS"
-You will see four addresses under "Personal Feeds". You want to insert them in the following code that you need to run on the backend machine..."

Once I found my custom RSS urls I went back to the command line. The next step was to use these custom urls to insert a couple of records into my "mythconverg" database, and its "netflix" table.

I had not previously assigned a root password to Mythbuntu's MySQL server. So, I assigned one like this:

$ mysqladmin -u root password <newpassword>

Then I fired up the mysql client:

$ mysql -u root -p

It asked for my password. I typed it in and pressed the ENTER key. The MySQL client welcomed me:

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 87
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

After this I entered the following at the MySQL client prompt. Your custom "Queue" url replaces RSS-Q in the command below:

mysql> insert into mythconverg.netflix (name, category, url, ico, updated, is_queue) values ('Queue','NetFlix', 'RSS-Q','http://cdn.nflximg.com/us/icons/nficon.ico', null, 1);

It should return:

Query OK, 1 row affected (0.00 sec)

If it doesn't the client complains about a syntax error instead. Make sure that you enter it EXACTLY, except for the substitution of course. The MySQL client is very picky about what it will accept for input.

One more time. This time I substituted my custom "Most Recent Rental Activity" RSS url for RSS-H in the following command:

mysql> insert into mythconverg.netflix (name, category, url, ico, updated, is_queue) values ('History','NetFlix', 'RSS-H','http://cdn.nflximg.com/us/icons/nficon.ico', null, 2);

Again, the client returned:

Query OK, 1 row affected (0.00 sec)

After that I typed:

mysql> exit

...to get out of the MySQL client. Then I fired up mythfrontend, navigated to the Info Center and admired my handiwork.

It took me awhile to figure this out. I hope this makes it easier for someone else.

---

### Post by penbrock on 2008-11-27
THANK YOU!!!
This has been driving my nuts. I just wonder why these records are not added to the install so we can just plugin our information

---

### Post by carltonb on 2008-12-28
I have installed Mythbuntu and found this thread on how to set up a password for Netflix.

Would I use the same directions for setting this up

Thanks
CarltonB

---

### Post by ctucker10 on 2008-12-28
@carltonb

Following the instructions I posted above will enable you to view your Netflix account info in mythfrontend.

I never got all of the Netflix functions to work in the frontend i.e. adding a selection to my queue, but at least I can browse the RSS feeds, see what's next in my queue, etc.

I hope the instructions make sense...it appears that they worked for at least one person other than me. Give it a shot...see what happens...let us know how it turns out. Cheers.

---

### Post by IceCap on 2009-03-09
I had an error in my entry into mysql database.  How do I correct it?  Or, what are the names of the fields that got the data?  If I know the field names then I think I can fix it.

  Thanks

  IC

---

### Post by ctucker10 on 2009-03-09
Most often commands return errors because of typographical errors in my experience. Assuming, of course, that the syntax is correct. Please make sure that there are no typos in the part of the command that contains your custom substitution. Make sure that you use single quotes around the substitution.

If you've already done all that. I dunno...I wish I could help more.

---

### Post by IceCap on 2009-03-09
Sorry, this was confusing.  The command went fine, I had an error in my RSS feed URL.  So now the entry is there in mysql  I can't repeat it.  I need to modify it.

  Thanks

  IC

---

### Post by IceCap on 2009-03-12
So can someone help me with replacing the Netflix entry in mysql?  I tried to fixed but I can't seem to find the correct command for it.

 Thanks

  IC

---

### Post by abstraktion on 2009-03-12
I use phpmyadmin and do it through the browser.
This will  help install: [http://ubuntuforums.org/showthread.php?t=889753]("http://ubuntuforums.org/showthread.php?t=889753").
Then goto the mythconverg database and the netflix table to make the changes.

Eric

---

### Post by abstraktion on 2009-03-12
> **ctucker10 said:**
> Entering my Netflix info was not as straightforward as it could have been, I managed to do it this way...via the command line.

I went to:

[https://help.ubuntu.com/community/MythFlix](https://help.ubuntu.com/community/MythFlix)

...for general instructions, but they didn't work (for me) verbatim. The first thing I did was to run the following script, substituting my Netflix username (my e-mail address) and password:

$ /usr/share/mythtv/mythflix/scripts/netflix.pl -L <username> <password>

In my case, the script ran without errors. It returned "Code 200" so I moved on.

....
> 
I never got all of the Netflix functions to work in the frontend i.e. adding a selection to my queue, but at least I can browse the RSS feeds, see what's next in my queue, etc.

I also had this problem and fixed it by running ```
/usr/share/mythtv/mythflix/scripts/netflix.pl -q <queueName> -L <userid> <passwd>
``` and then using the same queue name in the database ```
  insert into netflix values ("Queue","NetFlix", '[YOUR QUEUE RSS URL]','http://cdn.nflximg.com/us/icons/nficon.ico', null, 1, '[YOUR QUEUENAME SPECIFIED ABOVE]');
``` Hope this helps others.

Reference:[http://svn.mythtv.org/trac/browser/trunk/mythplugins/mythflix/README]("http://svn.mythtv.org/trac/browser/trunk/mythplugins/mythflix/README")

eric

---

### Post by Nobodyspeshul on 2009-03-29
Hey gents, I tried these commands and got this output.
```

$ /usr/share/mythtv/mythflix/scripts/netflix.pl -q incoming -L <LOGINACCOUNT> <PASSWORD>
Status Code: 200
```

I'm removing the login names as usual.

```
mysql> insert into netflix values ("Queue","NetFlix", 'RSS FEED LINK','http://cdn.nflximg.com/us/icons/nficon.ico', null, 1, 'incoming');
ERROR 1046 (3D000): No database selected
```

So, what did I do wrong here?

---

### Post by abstraktion on 2009-03-30
> **Nobodyspeshul said:**
> Hey gents, I tried these commands and got this output.
```

$ /usr/share/mythtv/mythflix/scripts/netflix.pl -q incoming -L <LOGINACCOUNT> <PASSWORD>
Status Code: 200
```

I'm removing the login names as usual.

```
mysql> insert into netflix values ("Queue","NetFlix", 'RSS FEED LINK','http://cdn.nflximg.com/us/icons/nficon.ico', null, 1, 'incoming');
ERROR 1046 (3D000): No database selected
```

So, what did I do wrong here?

Try
```
mysql> insert into mythconverg.netflix values....
```

---

### Post by Nobodyspeshul on 2009-03-30
Here's the screenshot from my phpadmin on my netflix database.

I'm pretty sure I added in the correct values, but things don't seem to be working even when I go to check out my queue through MythFlix.

Thanks for the help.

```
mysql> insert into mythconverg.netflix values....
```

Just gives me the output:

->

Not sure what values to input and I don't want to screw up my mysql database any more than I did before.

---

### Post by abstraktion on 2009-03-30
> **Nobodyspeshul said:**
> Here's the screenshot from my phpadmin on my netflix database.

I'm pretty sure I added in the correct values, but things don't seem to be working even when I go to check out my queue through MythFlix.

Thanks for the help.

```
mysql> insert into mythconverg.netflix values....
```

Just gives me the output:

->

Not sure what values to input and I don't want to screw up my mysql database any more than I did before.

The pic is way to small to see...

---

### Post by abstraktion on 2009-03-30
That screen won't show any thing other than you having the tables in the db. Click on the SQL tab at the top and the go on the bottom right of the next screen. Then post the output from that.

---

### Post by Nobodyspeshul on 2009-03-30
Here's the output.

[IMG]http://i114.photobucket.com/albums/n270/scottyz79/Go.jpg[/IMG]

Should I manually change the values for Queue and History?

---

### Post by abstraktion on 2009-03-30
> **Nobodyspeshul said:**
> Here's the output.

[IMG]http://i114.photobucket.com/albums/n270/scottyz79/Go.jpg[/IMG]

Should I manually change the values for Queue and History?

The queue url should be changed to something like
```
http://rss.netflix.com/QueueRSS?id=P00000000000
```

The queue "is_queue" should be 1

The queue "queue" should be your queue name

That should fix the queue...To fix history...

The url should be like 
```
http://rss.netflix.com/TrackingRSS?id=P000000000
```

is_queue should be 2

and queue should be the same name as above.

Let me know if that worked :)

---

### Post by Nobodyspeshul on 2009-03-30
That worked wonderfully.

Here's how everything looks right now.

Doesn't look like I'm able to add things into my queue yet..I'll look back on this thread and see how to adjust that.

[IMG]http://i114.photobucket.com/albums/n270/scottyz79/Go-1.jpg[/IMG]

---

### Post by jdeslip on 2009-06-13
The netflix.pl script does not seem to work for me anymore... I have run it a hundred times and it creates the required netflix.cookies file in .mythtv/MythFlix, but updating/rearranging my queue still doesn't work.  If I remember right the created netflix.cookies file used to have a field that said NetflixShopperSecret, but that is missing from any files I try to generate now.  Can I somehow copy a cookie from firefox or something?

---

