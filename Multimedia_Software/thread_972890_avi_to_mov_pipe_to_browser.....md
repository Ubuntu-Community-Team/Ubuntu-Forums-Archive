---
title: "avi to mov pipe to browser....?"
date: 2008-11-06
forum: Multimedia Software
---

### Post by brownrl on 2008-11-06
Ok

Here is one that should be fun!!!

I have an iPhone...  ya ya I know enough already... No flash.

I also have an Ubuntu media center with a web server.

When I torrent an .avi movie I would like to be able to 'preview' it on my iPhone without using a flash thingy.

iPhone can play mov or mp4... streams...

So using either ffmpeg or mencoder I would like to read in the avi file and output as a mov file.

Lastly, I would like to do this in a PHP page...

So far I can convert the file to another file...

Not very helpful because then I have to wait for the conversion to happen completely. Also I don't see how to make ffmpeg output to a pipe. It has to be possible?

So I want to do something like this:

```

<?php

   $file = "acitest.avi";

   header( "YADA YADADA THIS IN AN MOV FILE..." );

   passthru( "ffmpeg somestuff to convert $file to an mov" );
   
   exit( 0 );
?>

```

---

