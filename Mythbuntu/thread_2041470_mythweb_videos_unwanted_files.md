---
title: "mythweb videos unwanted files"
date: 2012-08-12
forum: Mythbuntu
---

### Post by seijirou on 2012-08-12
How do I restrict what files are returned as a result of scan collection?   :confused:

My video folders have a lot of supplementary data files such as .xml, .txt, .log, .edl, etc.  All of these files are listed and the only way to distinguish what is what is to hover the mouse over the download link to see if the filename ends with a video extension (mpeg, avi, m4v, etc.)

Thanks

---

### Post by tgm4883 on 2012-08-12
> **seijirou said:**
> How do I restrict what files are returned as a result of scan collection?   :confused:

My video folders have a lot of supplementary data files such as .xml, .txt, .log, .edl, etc.  All of these files are listed and the only way to distinguish what is what is to hover the mouse over the download link to see if the filename ends with a video extension (mpeg, avi, m4v, etc.)

Thanks

Move them out of your media directory? If they aren't media, why are they in that directory?

---

### Post by seijirou on 2012-08-12
> **tgm4883 said:**
> Move them out of your media directory? If they aren't media, why are they in that directory?

They are supplementary files and serve a purpose, just not in context of mythtv/mythweb.

My guess/hope is that a php script reads the folders and sucks in every file.. I'd like to modify that to only grab files with certain extensions.   However I am extremely weak in PHP and I haven't been able to find that function to modify... assuming my guess is true.  I could use a hand.

thanks.

---

### Post by Rotak on 2012-08-12
AFAIK, the scan is done by the backend, as if you'd check the videos folder for changes from within MythVideo. Don't think the "problem" is located within the PHP code.

---

### Post by seijirou on 2012-08-12
> **Rotak said:**
> AFAIK, the scan is done by the backend, as if you'd check the videos folder for changes from within MythVideo. Don't think the "problem" is located within the PHP code.

That may be, I'm not sure.

What I think I know is that /var/www/mythtv/modules/video/tmpl/default/video.php uses PHP to create the HTML for the videos section in mythtv.

I have been able to correlate some of the lines in that file with what I see when I view source in the videos section of mythtv.

For example I believe this line is what creates the green Scan Collection button.  I look for that because until you click it, absolutely nothing shows up in mythweb regardless of what exists in your folders.  This is one of the reasons I think the contents of the videos under mythweb is populated with a PHP function and/or script.

```
<span style="float: right"><input type="button" value="<?php echo t('Scan Collection'); ?>" class="submit" onclick="scan()"></span>
```

In that line, onclick="scan()" stands out.

Farther up in the same file is the scan() function.

```
function scan() {
        ajax_add_request();
        new Ajax.Request('<?php echo root_url; ?>video/scan',
            {
                method:    'get',
                onSuccess: reload
            });
    }
```

But beyond that i'm lost.  I can't find the ajax_add_request() function in this file, I'm guessing it comes from somewhere else.  I also don't know what "new Ajax.Request(" is doing.  I'm not a programmer so I don't really know where to go from  here.

---

### Post by seijirou on 2012-08-12
Okay, I have the answer.

My initial approach was to try to change the;
*grab everything, give me everything grabbed*... behavior in to... *grab **select** things, give me everything grabbed*

That went nowhere fast.  I now think the scan() function basically just ran the scan.php file in the same directory as the video.php file.  The contents of which was, as Rotak's gut told him, a Backend call of "SCAN_VIDEOS".  Point Rotak. :KS

So I decided to change my approach to
*grab everything, give me **select** things*

Being pretty sure that video.php dynamically creates the HTML in the video section of mythweb I looked in there again and found this.

```
<?php
    foreach ($All_Videos as $video) {
?>
```

I guessed that $All_videos was an array or hash or some blob representing the results of "SCAN_VIDEOS".  So with that assumption looking a little further down I see this.

```
 <a href="<?php echo $video->url; ?>"><?php echo html_entities($video->title); ?>
```

Going back to view source on the mythweb webpage I can see that in the HTML $video->url is replaced by the full path to that file.  Now I've got some file extensions I can work with! :guitar:

I do some Googling on regex in php and come up with some examples on preg_match().  After a bit of fiddling to syntax and silly mistakes because I don't know wtf I'm doing, this is my final result and it works.

```
<?php
    foreach ($All_Videos as $video) {
        if (preg_match("/\.avi$/", $video->url) ||
                preg_match("/\.mpg$/", $video->url) ||
                preg_match("/\.mpeg$/", $video->url) ||
                preg_match("/\.ts$/", $video->url) ||
                preg_match("/\.ogm$/", $video->url) ||
                preg_match("/\.m4v$/", $video->url) ||
                preg_match("/\.mp4$/", $video->url) ||
                preg_match("/\.mkv$/", $video->url)
        ) {
?>
```

One two skip a few... and add the extra } at the bottom.

I now only see files that end with the extensions specified.  :popcorn:

---

