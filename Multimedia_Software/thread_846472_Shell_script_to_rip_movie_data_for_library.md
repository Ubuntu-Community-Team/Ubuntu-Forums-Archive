---
title: "Shell script to rip movie data for library"
date: 2008-07-01
forum: Multimedia Software
---

### Post by Rizla on 2008-07-01
Hey guys, maybe someone can help me out with a general movie question.  I'm building out my DVD library that i'm using to access via a NMT (network media tank, awesome BTW).  Currently, it doesnt have a very nice frontend for accessing movie meta data, but it does give you the ability to create your own custom listing via a webpage.

My goal is to populate my dvd list using data grabbed from IMBD, or collectorz.com (ex: [http://www.collectorz.com/connect/movies/25th-hour-2002/]("http://www.collectorz.com/connect/movies/25th-hour-2002/")

SO with that said, has anyone set foot down this path before?

Right now the way i envision my route is to wget the index page of the movie i want (see output of the link).  Grab the relevant data via a regex expression.  Place the data in a comma seperated file, then run a script that parses that data into a local db on my webserver.  Then when my NMT accesses my movie listing, spit out the relevant data.

I'm a beginner with regex, but have a book that will probably get me through this exercise.  Just wondering if anyone has done this already.


OR is there a program that does this?  Im basicaly looking for cover art, plot summary, actors, and other general data.

---

