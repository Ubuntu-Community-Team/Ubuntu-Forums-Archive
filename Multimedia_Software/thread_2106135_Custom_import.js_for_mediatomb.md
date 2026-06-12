---
title: "Custom import.js for mediatomb"
date: 2013-01-18
forum: Multimedia Software
---

### Post by natomb on 2013-01-18
Hello there,

I dislike the builtin media parser results of mediatomb because it will create lots of subfolders that are tiresome to navigate through on my TV set. Thus, I have modified the import.js script file the following way:

```

function addVideo(obj)
{
    var dir = getRootPath(object_root_path, obj.location);

    if (dir.length > 0)
    {
        var chain = new Array('Video');
		var lastPath = getLastPath(dir);
		if (lastPath.length < 1) { chain = chain.concat('_Neu'); }
		else if (lastPath = '_Movies') { chain = chain.concat('Filme'); }
		else { chain = chain.concat(lastPath); }

        addCdsObject(obj, createContainerChain(chain));
    }
}

```

Then, I restarted mediatomb on a fresh database, added my folders to scan and the result was that mediatomb still builds a lot of subfolders, ignoring my import.js file. After a search in google I realied that I have to change the parser type in the config.xml file from builtin to js. Ok, done, restarting mediatomb.

Now the surprise: mediatomb did not start and in the log file it complains that JavaScript support was not compiled in. To solve, I should install all the build tools required to compile software, download the source code and build mediatomb by myself.

Unfortunately, I am very inexperienced in coding and also do not want to use anything on my ubuntu machine that is not managed through apt. Thus, is there a solution to customize the way mediatomb creates the virtual elements, i.e. without building lots of new path, but still rely on the mediatomb version offered through apt?

Thank you very much
  Bjoern

---

