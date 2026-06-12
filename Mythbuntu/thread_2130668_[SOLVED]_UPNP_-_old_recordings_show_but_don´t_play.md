---
title: "[SOLVED] UPNP - old recordings show but don´t play after migration"
date: 2013-03-30
forum: Mythbuntu
---

### Post by flecki on 2013-03-30
I successfully migrated my mythtv system(front+backend in one machine) to a new hardware.

The new machine based on a brand new core 3 at 3,3 Ghz with integrated graphics works like a charm at openGL high profile even on hd, uses 30-38 Watts and is absolutely silent.

I backed up the old DB and restored it on the new machine - i moved the recordings to the new machine but to a different directory(changed this in backend setup) /var/lib/mythtv/recordings 

So far everything works fine and mythtv finds and plays all recordings.

Two things are still open - in mythweb i don´t see preview pictures for the old recordings(the new ones work) although the files are there - this does not bother me much though...

The worst thing is that with UPNP using different clients i can _see all _recordings but only play those that are new - i have no idea why as there is little documentation for troubleshooting.

I can only imagine that maybe upnp-server stuff stored the old location and filenames somewhere and does not renew it´s information based on the new locations. So once the upnp clients do try to access the files they fail...

I would be happy for every tip you can give me on how to make upnp work with my old recordings too

Marcus

---

### Post by tgalati4 on 2013-03-30
I don't have a mythtv setup, but generally you would wipe the old database and rescan completely to create a new database.  You will have to search for the commands to do that.  On mediafly or firefly, there is a button on the admin page to rescan the library.

---

### Post by flecki on 2013-03-30
This would not help as i want to keep the metadata information for my recordings and rules etc. which are - as i understand it - in that database.

I am not talking about videos here - only tv-recordings.

And all is working well when using mythth-frontend to play the stuff - only external upnp-clients can only access the recordings after the hardware change not the ones before that date.

As i said i think the UPNP-server has stored the old directory locations and names somewhere else and needs a forced rescan - i just don´t know how to do that.

The fun is - i can see all those recordings(old AND new ones) with every Upnp client i use - but i can only play the new ones since the change.

Marcus

---

### Post by tgalati4 on 2013-03-30
Make a dummy directory in the old location with the correct name.  Use a symbolic link to link the dummy directory to the new location.

```
sudo ln -s /var/lib/mythtv/recordings /var/lib/mythtv/oldirectorynamewithcorrectlocationbeforeicompletelymungedmysystem
```

---

### Post by flecki on 2013-03-31
Did not work .... seems not to be a directory issue. Maybe old IP or hostname settings stored ?

Unfortunately i can´t locate any documentation on how(or where) UPNP stores it´s informations...

---

### Post by flecki on 2013-04-02
Found an old post where a guy has similar problems with remote frontends after migrating his backend.

Seems it has to do with hostnames stored in the recorded table that will be used as a reference for locating files by other frontends and probably UPNP too.

I will try to look into that table and change one of the old recordings hostnames for a test to see if that is the case.

Marcus

----Update----

Installed SquirrelSQL and activated remote acces on MYSQL via jdbc - now i see the database but....

Strangely the recorded table has 421 rows which is the correct number of recordings - only if i try to look into the table i only get 100 or so displayed - i need to look into this or ask someone who knows his ways around SquirrelSQL

----Update----

Squirrel semms to have an encoded 100 row limit - changed that - now i can at least see all the mess :-)

Changing the hostname in the recorded table to the new one did not change the UPNP behaviour - now trying to get something useful out of the backend log

---

### Post by tgalati4 on 2013-04-04
I admire your persistance in trying to solve this problem.  Why did the hostnames change when you built the new server?  Is it possible to simply change the name of the server back to the old name to see if it works?

---

### Post by flecki on 2013-04-05
Well - at start(while migrating) i had both systems running and thought it was a good idea. I sepaerated them in subnets so they could not see each other so it would not have been necessary though...

Once you have the system installed and running with a new hostname and do a database drop and restore from the old one on the new machine you seem to end up with a database with entries for both hostnames - changing back now is too late.

I used the changing hostname script described on: [http://www.mythtv.org/wiki/Backend_migration]("http://www.mythtv.org/wiki/Backend_migration") but still find old hostnames and in some tables the "OLDHOSTNAME" placeholder that indicates some issues ass far as i can tell from some posts - still the systems works - only upnp does not for the old recordings.

I will now analyse the backend.log and i am chasing up a tip about upnp using the startupdir entry in the video table too(easy to check that but not sure about it as the new recordings DO work and are in the same path) - i´ll keep posting what i find.

As we say in austria - afterwards you are always more clever :-)

---

### Post by flecki on 2013-04-05
Stupid, stupid, stupid.....

As i found nothing whatsoever in the logs i stumbled over a permissions issue when trying to download an old recording in mythweb - and then ..... A BLINDING FLASH OF THE OBVIOUS !!

Permissions !!

Seems when copying if forgot to edit the mythv group grouprights on the files in the recording directory(upnp needs this rights) - the new created files got them of course as mythtv creates them....

And of course your upnp clients don´t give feedback on why they could not play the file...mythweb does.

At least i learned A LOT about Mythtv database tables :-) (you need to have the new hostname in them for sure)

I really deserve the idiot of the day award....

---

