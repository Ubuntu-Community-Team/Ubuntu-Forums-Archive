---
title: "f-spot export tags"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by taphos on 2008-03-16
I've got a collection of photos in raw format
I like to use f-spot to manipulate the tags, but the problem is that I can not use the tag information in other programs. It is like if I loose the f-spot database (reinstall  linux or just copy photos to another location) my collection will be ruined.

I found a way to make the tag information to be kept forever not depending which platform or photo viewer I use.

Here is a small bash script which creates a directory with a tag name and creates symlinks to photos in this directory. This script is more like a hack, but probably it will inspire someone to write a similar extension for f-spot. I think such feature would be very useful.

Script requires sqlite3 package to be installed
```
sudo apt-get install sqlite3
```

```

#!/bin/bash                                                                                                                                                           
                                                                                                                                                                      
TAGNAME="Favorites"                                                                                                                                                   
DBFILE="$HOME/.gnome2/f-spot/photos.db"                                                                                                                               
                                                                                                                                                                      
function createDirectory {                                                                                                                                            
    if [ ! -d $1 ]; then                                                                                                                                              
        echo "Creating directory $1";                                                                                                                                 
        mkdir $1;                                                                                                                                                     
    fi                                                                                                                                                                
}                                                                                                                                                                     
                                                                                                                                                                      
function createSymlink {                                                                                                                                              
    if [ ! -e $2 ]; then                                                                                                                                              
        echo "Creating symlink $2";                                                                                                                                   
        ln -s $1 $2                                                                                                                                                   
    fi                                                                                                                                                                
}                                                                                                                                                                     
                                                                                                                                                                      
function checkDB {                                                                                                                                                    
    if [ ! -e $DBFILE ]; then                                                                                                                                         
        echo "f-spot database file not found $DBFILE"                                                                                                                 
        exit;                                                                                                                                                         
    fi                                                                                                                                                                
}                                                                                                                                                                     
                                                                                                                                                                      
checkDB;                                                                                                                                                              
                                                                                                                                                                      
for line in `sqlite3 $DBFILE <<SQL_ENTRY_TAG_1                                                                                                                        
SELECT p.directory_path, p.name                                                                                                                                       
FROM                                                                                                                                                                  
    tags t,                                                                                                                                                           
    photo_tags tp,                                                                                                                                                    
    photos p                                                                                                                                                          
WHERE                                                                                                                                                                 
    t.name='$TAGNAME' AND                                                                                                                                             
    tp.tag_id=t.id AND                                                                                                                                                
    tp.photo_id=p.id;                                                                                                                                                 
SQL_ENTRY_TAG_1`; do                                                                                                                                                  
    path=${line%|*}                                                                                                                                                   
    name=${line#*|}                                                                                                                                                   
    createDirectory $path/$TAGNAME;                                                                                                                                   
    createSymlink $path/$name $path/$TAGNAME/$name                                                                                                                    
done 

```

---

