# Git (and GitHub) Cheat Sheet

I published this as a blog post here: http://neuroplausible.com/github

## Create a New Repo
To create a new repository on GitHub go to: [https://github.com/new](https://github.com/new)

## Get Unlimited Private Repositories
Sign up for the academic/student pack on GitHub as many lab projects (also known as [repositories](https://help.github.com/articles/github-glossary/#repository) or repos) might need to be private (until publication, of course) and non-academics do not get unlimited free private ones.
[Sign up here](https://education.github.com/pack) — they only need your academic (.ac.uk or .edu, etc.) email address to associate it with your account.

## Clone
[Cloning](https://help.github.com/articles/cloning-a-repository/) means getting something for the first time.
So to download a whole repository for the first time (e.g., my's [gini repo](https://github.com/oliviaguest/gini)):
```
git clone git@github.com:oliviaguest/gini.git
```
This command makes a new directory called in this case: ```gini```. So you would need to change directory in order to see your newly downloaded files, i.e., ```cd```, like so:
```
cd gini
```
Then you can ```ls``` and ```ls -a``` to see all your files.
Feel free to actually ```clone``` my Gini repository as you cannot break it on GitHub since you do not have ```push``` rights.

## Add Files
[Adding](https://help.github.com/articles/adding-a-file-to-a-repository/) a file means asking version control to start watching it, but it is not yet in the history of your repository.
Just adding is not enough! All ```add``` does is say add this file to queue of files to be ```commit```ted (the next section). You can be explicit and name the files you want to add (all other files will not be added):
```
git add filename_1 filename_2... filename_n
```
Alternatively, you can add everything (except the things in your [```.gitignore```](https://help.github.com/articles/ignoring-files/) file):
```
git add -A
```
If you *just* ```add``` a file, it is not safe yet!
It *needs* to be ```commit```ted (next section) to be safely under version control!

## Commit Files
[Committing](https://help.github.com/articles/github-glossary/#commit) is adding all the files to version control, although *not* to the server (the next section).

To commit everything you have just ```add```ed:
```
git commit -m "I've just made some very dramatic changes"
```
For your files to be 100% safe make you *must* also ```push``` them (the next section).
Only ```commit```ting makes files be under version control on your local machine, e.g., your laptop, but they will *not* be accessible from another computer.

## Push Files
[Pushing](https://help.github.com/articles/pushing-to-a-remote/) ```commit```s, and therefore files, makes your changes enter into the version control system on the server as well as your local machine, so on GitHub (or [Overleaf](://overleaf.com), or [GitLab](://gitlab.com), or whatever server you are using).
So pushing is the superior form of backup and version control because it means that there are at least two copies of your work *and* its history: one local copy (the stuff you were just working on) and one server-side copy (what you just ```push```ed).

Once everything you need is ```add```ed and ```commit```ted, it is time to ```push```.
Many ```add```s may be in one ```commit```, many ```commit```s may be in one ```push```.
But there is no reason to limit yourself to pushing once a day.
Push as often as possible pretty much, is my advice.

Unsurprisingly, as you might guess, to ```push``` you type:
```
git push
```

## Check the Status
To check what is going on, what changes have been made, compare your local repository's status with that of the server, etc., type:
```
git status
```
This command will often tell you what you need to do given the current changes you have made, e.g., tell you you need to ```push``` your ```commit```s.
If you are unsure of anything, running ```git status``` should give you a hint about what the next command you want to run is.

<div class="float-right figure">
    <img class="image" src="{{ site.baseurl}}/img/posts/git-it-gurl.png" />
  <div class="figure-caption">
    "GIT IT, GURL. Because femmes belong in tech. Because femininity is not antithetical to engineering and logic. Because version control is important even for side projects with a team of 1 (you)." — <a href="https://twitter.com/sailorhg">sailorhg</a>.
    <a href="https://bubblesort-zines.myshopify.com/products/git-it-gurl-shirt?variant=37201321537">Get the t-shirt here!</a>
  </div>  
</div>

Importantly, if you have made server-side changes, i.e., you did some work on *machine A* and ```push```ed all that work to the server and now you are on a completely different *machine B* and need to get back to working on your repo, you need to tell the repo on this different machine B to check the server for changes.
This can be done by asking your local git, on B, to [fetch](https://help.github.com/articles/fetching-a-remote/) the changes from the server:
```
git fetch
```

Bear in mind that ```fetch``` *does not download any files*, it merely updates what your local git knows about the changes you did on machine A which you then ```push```ed to the server.
After ```fetch```ing, you may run ```git status``` as then the information on the differences between your local files and those on the server will be correct.
Otherwise, if you just run ```git status``` you risk getting the wrong information about what is on the server versus your local repo.

## Discard Changes
If you made some local changes and you do not want them around at all — you just want what is on the server, you can run:
```
git stash
```
This discards all your local changes that have *not* been ```add```ed or ```commit```ted.

## Pull Files
Pulling means getting stuff from the server. If you have made changes at work and then go home and want to continue working where you left off, you run:
```
git pull
```
Unsurprisingly, ```pull``` does the opposite of what ```push``` does. It downloads all the files you previously pushed to the server from work on your home computer.
