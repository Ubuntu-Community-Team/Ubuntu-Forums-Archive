---
title: "Tag-editing software nightmare - please help!"
date: 2009-06-15
forum: Multimedia Software
---

### Post by DGeeez on 2009-06-15
Helllllp! Tag editing in Ubuntu is driving me absolutely nutty! 

I spent hours editing MP3s which don't have consistent metadata with Rhythmbox, which looks like my only pre-installed option. After transferring them to my Sony Walkman phone, the data displayed horribly (the phone and player may very well be crap, but that alone can't explain the rest). So, I installed three programs which are MP3-specified through Synaptic, including EasyTag and Audio Tag Tool, and they won't even touch my MP3s at all! I've been to the Medibuntu site already to enable playback of all media, so is there more I need to do to make MP3 tag editing work in Ubuntu?

What's making me even crazier is that the Rythmbox list shows my files with perfectly-consistent, organized data, but this seems to exist only in Rhythmbox-world. With no functional programs other than my phone to compare the results, including the Nautilus browser (on Jackalope), I was afraid I would have to buy Windows just to edit my tags when I Googled up this script which enables display of tag information:[http://ubuntuforums.org/showthread.php?t=878683]("http://ubuntuforums.org/showthread.php?t=878683")

It works great, I recommend it for all who edit media tags, but now I don't like what it showed me - that the tag editing which I had done in Rhythmbox, and show results there, does not show at all in other browsers. 

1. Why is it that Ubuntu editors won't even look at MP3 tag data, except for Rhythmbox?

2. Is there a tweak somewhere which I need to install that would make all tag editors read MP3 data?

3. Why do changes to tag data with Rhythmbox seem to be ineffective on the actual file data, and can it actually be used to change original file data?

Please help, if you can - thank you!

---

### Post by CatKiller on 2009-06-15
I think it's fairly common for media players to put metadata in their own database of your music library. It means that you can have consistent metadata even if the files don't support tags themselves, or if they are on a read-only filesystem.

I've never had any problem with EasyTag. It handles ID3 tags fine. You can also get it to automatically fill in the tags based on the filename (or vice versa) using its scanner tool. Don't forget that you need to save the changes before you exit, either by manually hitting the save button or changing directory to get the prompt.

---

