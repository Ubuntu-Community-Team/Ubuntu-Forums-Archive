---
title: "[SOLVED] Shoutcast = no url"
date: 2008-09-22
forum: Mythbuntu
---

### Post by iitywygms on 2008-09-22
Love Mythbuntu so far.  This forum has been great!
Anyway.
When I try to listen to shoutcast i get a no url available.  It scans and starts to buffer but then it says no url.
When I click on top 25, same issue.  I have tried different genres and still no url is displayed.
Not sure what more information I can give.  Mythbuntu 8.04.1 latest updates.
I can browse apple movies with no issues.
If it means anything, when I put in my zip code for weather, I never get anything, no matter what zip code I use.  Firewall issue maybe???

---

### Post by tgm4883 on 2008-09-22
> **iitywygms said:**
> Love Mythbuntu so far.  This forum has been great!
Anyway.
When I try to listen to shoutcast i get a no url available.  It scans and starts to buffer but then it says no url.
When I click on top 25, same issue.  I have tried different genres and still no url is displayed.
Not sure what more information I can give.  Mythbuntu 8.04.1 latest updates.
I can browse apple movies with no issues.
If it means anything, when I put in my zip code for weather, I never get anything, no matter what zip code I use.  Firewall issue maybe???

Most likely, you need to update the shoutcast parser.  You can add the mythbuntu-testing PPA, which has updated parsers.  You will probably also have to delete ~/.mythtv/mythstream/parsers/

---

### Post by iitywygms on 2008-09-22
> **tgm4883 said:**
> Most likely, you need to update the shoutcast parser.  You can add the mythbuntu-testing PPA, which has updated parsers.  You will probably also have to delete ~/.mythtv/mythstream/parsers/

Forgive me I am a newb.  How do I update the shoutcast parser?

---

### Post by tgm4883 on 2008-09-22
> **iitywygms said:**
> Forgive me I am a newb.  How do I update the shoutcast parser?

Go here  [https://edge.launchpad.net/~mythbuntu-testing/+archive](https://edge.launchpad.net/~mythbuntu-testing/+archive)  Add these lines to /etc/apt/sources.list make sure you set the right release (hardy or intrepid).  apt-get update, then apt-get install mythstream-parser-shoutcast (there are other parser updates as well if you like).  Delete the directory I told you too.  Then it should work.

---

### Post by iitywygms on 2008-09-22
> **tgm4883 said:**
> Go here  [https://edge.launchpad.net/~mythbuntu-testing/+archive](https://edge.launchpad.net/~mythbuntu-testing/+archive)  Add these lines to /etc/apt/sources.list make sure you set the right release (hardy or intrepid).  apt-get update, then apt-get install mythstream-parser-shoutcast (there are other parser updates as well if you like).  Delete the directory I told you too.  Then it should work.

Appreciate the help.  However, now when I try to "play online streams" it opens but I have no choices now and it says cannot open --logfile.
Whats next?
Again, thanks for the help.

---

### Post by tgm4883 on 2008-09-22
> **iitywygms said:**
> Appreciate the help.  However, now when I try to "play online streams" it opens but I have no choices now and it says cannot open --logfile.
Whats next?
Again, thanks for the help.

Did you install the parser?

Whats the output of

dpkg -l | grep mythstream-parser-shoutcast

---

### Post by tgm4883 on 2008-09-22
I've also noted that the stream is configured incorrectly.  You must go into Utilities / Setup > Setup > Media Settings > MythStream Settings > Streams, then go down to Browse Shoutcast genres, hit tab, go down to *shoutcast/menu and change it to *shoutcast/menu.pl  then hit update and it should be working now.

---

### Post by iitywygms on 2008-09-23
> **tgm4883 said:**
> I've also noted that the stream is configured incorrectly.  You must go into Utilities / Setup > Setup > Media Settings > MythStream Settings > Streams, then go down to Browse Shoutcast genres, hit tab, go down to *shoutcast/menu and change it to *shoutcast/menu.pl  then hit update and it should be working now.

Everything in that area is empty.  In the upper left corner it says stations. nothing else on left side.
Then on the right hand side I have a area to add stream, steam folder, stream url, etc etc etc.  Under storage handling i have and option to use mythstream or stream in home directory.  I tried both options and noting changes.
Strange indeed...

---

### Post by tgm4883 on 2008-09-23
> **iitywygms said:**
> Everything in that area is empty.  In the upper left corner it says stations. nothing else on left side.
Then on the right hand side I have a area to add stream, steam folder, stream url, etc etc etc.  Under storage handling i have and option to use mythstream or stream in home directory.  I tried both options and noting changes.
Strange indeed...

Thats extremely strange.  I'm not at all sure how from deleting that parsers folder that you cleared out a table in the db.

Are you familiar with the db or phpmyadmin?  Can you look at the streams table and see if it exists or has anything in it?

---

### Post by iitywygms on 2008-09-23
> **tgm4883 said:**
> Thats extremely strange.  I'm not at all sure how from deleting that parsers folder that you cleared out a table in the db.

Are you familiar with the db or phpmyadmin?  Can you look at the streams table and see if it exists or has anything in it?

No, I am not familiar with that.  Can I just reinstall that portion of mythbuntu?  Can I reset it to original condition?

---

### Post by tgm4883 on 2008-09-23
> **iitywygms said:**
> No, I am not familiar with that.  Can I just reinstall that portion of mythbuntu?  Can I reset it to original condition?

It's worth a shot.  I'd completely remove (and purge) mythstream, then reinstall it and see if it gets that back.

---

### Post by iitywygms on 2008-09-23
Tried a purge and reinstalled it.  Still no luck.  
Any other ideas?

---

### Post by bmwman on 2008-09-23
I just noticed that I have the same problem. It was working fine couple of days ago, but now when I click on Browse Shoutcast it's saying "No URLs" :( The apple movie trailors and the other sections are working, but no Shoutcast.

---

### Post by tgm4883 on 2008-09-23
> **iitywygms said:**
> Tried a purge and reinstalled it.  Still no luck.  
Any other ideas?

When you go into mythstream, try hitting 0 0 on your remote, hopefully it will load the default setup

---

### Post by bmwman on 2008-09-23
> When you go into mythstream, try hitting 0 0 on your remote, hopefully it will load the default setup
That didn't change anything.

---

### Post by tgm4883 on 2008-09-23
> **bmwman said:**
> That didn't change anything.

That was meant for iitywygms, you will need to try what it says in post #7

---

### Post by bmwman on 2008-09-23
Thanks. I did that too. When I change to menu.pl i get random links and they're not in categories like Shoutcast Top25, Shoutcast Alternative, etc. It's kinda of unusable if you just get some links have no idea what kinda of stream that is.

---

### Post by tgm4883 on 2008-09-23
> **bmwman said:**
> Thanks. I did that too. When I change to menu.pl i get random links and they're not in categories like Shoutcast Top25, Shoutcast Alternative, etc. It's kinda of unusable if you just get some links have no idea what kinda of stream that is.

Unfortunatly, that is all I know on the issue.  I'm not the author of the parser, nor do I use.  I did test this and noticed the same thing that you did, that there are random links at the top, and that other links are below in categories.  You may have to email upstream about this, upstream is located here [http://home.kabelfoon.nl/~moongies/streamtuned.html](http://home.kabelfoon.nl/~moongies/streamtuned.html)

---

### Post by bmwman on 2008-09-23
It was working just fine before, I don't know what happened to it :(.
I'm wondering if purge/reinstall would fix it but I might lose even the Apple trailers and whatever else is left :(

---

### Post by iitywygms on 2008-09-23
> **tgm4883 said:**
> When you go into mythstream, try hitting 0 0 on your remote, hopefully it will load the default setup

okay did that.  when i hit 0 0 nothing happened, but when i hit 0 9 it brought up a few things, apple movie trailers was one.  Tried that and it worked.  tried to browse shoutcast.  again it said no url.  reinstalled the shoutcast plugin and tried again.  still get no url.
But at least we are making progress.  I really appreciate your effort.  Any more ideas? anybody else have any suggestions?

---

### Post by tgm4883 on 2008-09-23
> **bmwman said:**
> It was working just fine before, I don't know what happened to it :(.
I'm wondering if purge/reinstall would fix it but I might lose even the Apple trailers and whatever else is left :(

My guess is that it was the shoutcast parser that needs updating.  You can grab it as suggested above, but The same strange outcome could happen to you where you would lose everything.

---

### Post by gfowler on 2008-09-24
> **bmwman said:**
> I just noticed that I have the same problem. It was working fine couple of days ago, but now when I click on Browse Shoutcast it's saying "No URLs" :( The apple movie trailors and the other sections are working, but no Shoutcast.

Shoutcast changed the format, so the parser no longer works. The mythstream author has an updated parser.  I just updated the files in /usr/share/mythtv/mythstream/parsers/shoutcast/

I would advise saving a backup in the event ' gremlins ' live there.

Here's what I did and it worked for me with mythbuntu.  Go to the mythstreams website

[http://home.kabelfoon.nl/~moongies/streamtuned.html#dl](http://home.kabelfoon.nl/~moongies/streamtuned.html#dl) 

download shoutcast2.tar.gz and extract the files and replace files in 
 /usr/share/mythtv/mythstream/parsers/shoutcast/

restore the original permissions and you should be good to go, or at least that worked for me.  

tgm's method would be the better for long term as shoutcast is likely to do this again and manual updating can be a pain as well as fraught with ' Ut Oh's'

Jerry

---

### Post by tgm4883 on 2008-09-24
> **gfowler said:**
> Shoutcast changed the format, so the parser no longer works. The mythstream author has an updated parser.  I just updated the files in /usr/share/mythtv/mythstream/parsers/shoutcast/

I would advise saving a backup in the event ' gremlins ' live there.

Here's what I did and it worked for me with mythbuntu.  Go to the mythstreams website

[http://home.kabelfoon.nl/~moongies/streamtuned.html#dl](http://home.kabelfoon.nl/~moongies/streamtuned.html#dl) 

download shoutcast2.tar.gz and extract the files and replace files in 
 /usr/share/mythtv/mythstream/parsers/shoutcast/

restore the original permissions and you should be good to go, or at least that worked for me.  

tgm's method would be the better for long term as shoutcast is likely to do this again and manual updating can be a pain as well as fraught with ' Ut Oh's'

Jerry

Would you mind telling me if you have a ~/.mythtv/mythstream/parsers/shoutcast

---

### Post by gfowler on 2008-09-24
> **tgm4883 said:**
> Would you mind telling me if you have a ~/.mythtv/mythstream/parsers/shoutcast

Doesn't sound promising:)!

Should I stay on shore away from the big waves.

Answer: yes

---

### Post by tgm4883 on 2008-09-24
> **iitywygms said:**
> okay did that.  when i hit 0 0 nothing happened, but when i hit 0 9 it brought up a few things, apple movie trailers was one.  Tried that and it worked.  tried to browse shoutcast.  again it said no url.  reinstalled the shoutcast plugin and tried again.  still get no url.
But at least we are making progress.  I really appreciate your effort.  Any more ideas? anybody else have any suggestions?

Very strange.

Can you go to the master backend, open up a command line and do (make sure to use your mythtv password

```

mysql -u mythtv -p mythconverg

```

once logged into the mysql server do

```

select * from streams
/g

```

Hopefully after you do that you should see some output like

> 
| Video         | YouTube top viewed today                         | [http://youtube.com/rss/global/top_viewed_today.rss](http://youtube.com/rss/global/top_viewed_today.rss)                                   | Voor andere feeds zie youtube                            | youtube/feed        | 
| stream lists  | Icecast list                                     | [http://dir.xiph.org/yp.xml](http://dir.xiph.org/yp.xml)                                                           | Harvested with icecast.pl script                         | icecast             | 
| stream lists  | OperaCast list                                   | [http://www.operacast.com/opstations.htm](http://www.operacast.com/opstations.htm)                                              | Stationlist from [www.operacast.com](www.operacast.com)                       | operacast           | 
| stream lists  | Operanut list (default parser)                   | [http://operanut.com/radio.htm](http://operanut.com/radio.htm)                                                        | Some dead streams                                        |                     | 
| stream lists  | Robins BBC parser                                | ask the parser :)                                                                    | BBC parsing by Robin Gilks                               | *bbc/robins_links   | 
+---------------+--------------------------------------------------+--------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------+



---

### Post by bmwman on 2008-09-24
I got it fixed! :D
I sent email to the developer and he replied to me. Apparently there was a change in the Shoutcast site and that's why it stopped working. Here is the new script that needs to be used as of September 15. Just unpack it in your ~/.mythtv/mythstream/parsers/ directory and overwrite the existing one. Mine is back to working :)

Attached is the new script.

---

### Post by iitywygms on 2008-09-24
> **bmwman said:**
> I got it fixed! :D
I sent email to the developer and he replied to me. Apparently there was a change in the Shoutcast site and that's why it stopped working. Here is the new script that needs to be used as of September 15. Just unpack it in your ~/.mythtv/mythstream/parsers/ directory and overwrite the existing one. Mine is back to working :)

Attached is the new script.

And the prize goes to bmwman.  Thank you so much.

---

### Post by bmwman on 2008-09-24
I'm actually suprised that more people haven't had this issue yet. I don't know if this can be pushed thru the system updates.

---

### Post by tgm4883 on 2008-09-24
> **bmwman said:**
> I'm actually suprised that more people haven't had this issue yet. I don't know if this can be pushed thru the system updates.

It's supposed to be able to, thats why I had the OP delete .mythtv/mythstream/parsers

I can push system updates to the mythstream directory, but I can't push them to the users home directory, and the parsers reside in both ares, with the home directory parsers taking precedence.

---

### Post by iitywygms on 2008-09-24
> **iitywygms said:**
> Everything in that area is empty.  In the upper left corner it says stations. nothing else on left side.
Then on the right hand side I have a area to add stream, steam folder, stream url, etc etc etc.  Under storage handling i have and option to use mythstream or stream in home directory.  I tried both options and noting changes.
Strange indeed...

This is still the case.  I still have to press 0 9 on the remote before anything will work.  Is it possible to fix that?
Thanks for the help.

---

### Post by tgm4883 on 2008-09-25
> **iitywygms said:**
> This is still the case.  I still have to press 0 9 on the remote before anything will work.  Is it possible to fix that?
Thanks for the help.

Did you do what it says in post 25

---

### Post by iitywygms on 2008-09-26
> **tgm4883 said:**
> Did you do what it says in post 25

My password for mythtv is not working????  I use the one for mythtv right?
I got it by looking in the general settings.  I even tried my password.
????????

---

### Post by tgm4883 on 2008-09-26
> **iitywygms said:**
> My password for mythtv is not working????  I use the one for mythtv right?
I got it by looking in the general settings.  I even tried my password.
????????

My bad, you are probably not on you mysql server machine.  You need the host flag also.  Try this

```
mysql -h *hostname* -u mythtv -p mythconverg
```

Then do the rest of that post.

---

### Post by iitywygms on 2008-09-26
Dumb question

What is my hostname?

---

### Post by tgm4883 on 2008-09-26
> **iitywygms said:**
> Dumb question

What is my hostname?

That would be the name of the backend server, you could also use your ip address of the backend system

---

### Post by iitywygms on 2008-09-27
> **tgm4883 said:**
> That would be the name of the backend server, you could also use your ip address of the backend system

I tried using my myth backend name, and that did not work.  I tried using the ip address, that did not work either.  I know I have the password correct.  Am I missing something?
I feel kinda dumb asking these question but I know nothing about mysql.
thanks

---

### Post by iitywygms on 2008-09-29
bttt

---

### Post by iitywygms on 2008-10-08
Okay, I have time to work on this.

mysql> select * from streams
    -> \g
Empty set (0.00 sec)

What else should I try???

---

### Post by tgm4883 on 2008-10-09
> **iitywygms said:**
> Okay, I have time to work on this.

mysql> select * from streams
    -> \g
Empty set (0.00 sec)

What else should I try???

Well thats no deal.  Those parsers that I had you delete couldn't have emptied your db table, so somehow that didn't get populated or when you deleted the parsers you also removed every stream from mythstream.  I can dump my table here and give you a copy if you like?

---

### Post by tgm4883 on 2008-10-09
Here's a copy of that table.

---

### Post by iitywygms on 2008-10-09
I appreciate that.  What should I do with this table?
Thanks.

---

### Post by iitywygms on 2008-10-10
bump

---

### Post by dcwandj on 2008-10-11
> **bmwman said:**
> I got it fixed! :D
I sent email to the developer and he replied to me. Apparently there was a change in the Shoutcast site and that's why it stopped working. Here is the new script that needs to be used as of September 15. Just unpack it in your ~/.mythtv/mythstream/parsers/ directory and overwrite the existing one. Mine is back to working :)

Attached is the new script.

Thanks bmwman.  I think that I need this fix too since I can't get any Shoutcast streams at all.  However, since I'm a newb with linux commands I'm a bit leery of how to do an un-pack and install etc.  Would you be able to post a step by step for the fix you give above or point to one that's already published (I haven't found one tho)?

Follow-up:  Did some research and figured it out.  BTW works great! now I have shoutcast back!

D

Thanks

---

### Post by iitywygms on 2008-10-13
bump

---

### Post by iitywygms on 2008-10-16
one last hopeful bump.

---

### Post by tgm4883 on 2008-10-17
> **iitywygms said:**
> one last hopeful bump.

Sorry about the delay.  You should be able to just do 

```
mysql -u root -p mythconverg < streams.sql.gz
```

---

### Post by iitywygms on 2008-10-18
Fixed, thank you much.

---

### Post by thedarkone on 2009-03-18
i can not get it to work i keep getting no stream error

---

### Post by guyverix on 2009-03-19
> **iitywygms said:**
> 
If it means anything, when I put in my zip code for weather, I never get anything, no matter what zip code I use.  Firewall issue maybe???

I was running into this problem as well, so I got annoyed and started using major cities that are close by, and that DID work for me.  If you try to do this, try the major cities without the comma state at the end, and you might have luck with it.

Chris

---

