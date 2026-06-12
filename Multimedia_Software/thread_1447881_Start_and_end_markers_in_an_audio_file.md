---
title: "Start and end markers in an audio file"
date: 2010-04-05
forum: Multimedia Software
---

### Post by liddlem on 2010-04-05
Hi Folks 
I did post this thread on the Mono forum site too - sorry.
 
I am a total newbie to Linux, Ubuntu, Mono, C# and audio editing - but keen to learn. 
 
I have a project where I would like to display images and play an audio file. (simple enough) 
 
However, I would like to pre-determine when the image should change, based on where the playhead is currently situated within the audio file. 
In effect, the application will read a database (or XML) which contains "Audio_FileName", "Start_Point", "End_Point" and "Image_Name". 
As the playhead reaches "End_Point", the pointer moves the the next record in the DB/XML, changes the image and continues playing (or skips ahead to the next "Start_Point" if its different) 
 
I have this all working in my proof-of-concept tool, (once the data is in the DB) but I am making MANY instances of the same thing, so I would like an IDE which has both an audio editor and database on screen. 
1. Open the Audio file and select the relevant portion for the image. 
2. Click a button that writes the "Start_Point" and "End_Point" to my database. 
(Inserting the start and end point by hand is REALLY laborious.) 
 
Is this do-able in Mono / C#?

---

