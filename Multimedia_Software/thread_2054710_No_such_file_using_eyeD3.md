---
title: "No such file using eyeD3"
date: 2012-09-07
forum: Multimedia Software
---

### Post by alfirdaous on 2012-09-07
Hello everybody,

I am trying to remove id3v1 tags using eyeD3 command with PHP:

[PHP]
<?php
$remove = "/usr/bin/eyeD3 --remove-lyrics --remove-v1 001.mp3";
 //echo $remove.'<br />';
        $removeTags = exec($remove);
        
        if($removeTags)
        {
            echo '<font color="green"/>Tag removed successfully</font><br />';
        }
        else
        {
            echo '<font color="red"/>Tag failed to be removed</font><br />';
        }

?>

[/PHP]every time it failed, even though the file 001.mp3 is on the same directory, this is DOES NOT work on server, but in local machine, it WORKS, a command line used also, it WORKS.

Error says: 

> 
[Sat Sep 08 04:26:46 2012] [error] [client IP] /usr/bin/env: python: No such file or directory, referer: [http://site.com/Downloads/Medias/MP3](http://site.com/Downloads/Medias/MP3)



any idea about this issue.

Thx in advance

---

### Post by alfirdaous on 2012-09-12
solution: [https://bugs.launchpad.net/ubuntu/+source/eyed3/+bug/307345](https://bugs.launchpad.net/ubuntu/+source/eyed3/+bug/307345)

---

