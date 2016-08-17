# Raphael Augustos. [![Analytics](https://ga-beacon.appspot.com/UA-73784599-1/welcome-page)](https://raugustos.github.io/)

[![MIT Licence](https://badges.frapsoft.com/os/mit/mit.svg?v=103)](https://opensource.org/licenses/mit-license.php)
[![stable](http://badges.github.io/stability-badges/dist/stable.svg)](http://github.com/badges/stability-badges)
[![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.png?v=103)](https://github.com/ellerbrock/open-source-badge/)


I'm using this theme like my personal profile but if you want to use to you, please, feel free!


## My Personal Profile 

http://raphaelaugustos.com.br/

## Getting Started

If you're completely new to Jekyll, I recommend checking out the documentation at <http://jekyllrb.com> or there's a tutorial by Smashing Magazine.

I'll post step by step how to set up this theme coming soon in the section Blog.
#### Fork, then clone

**Fork** the repo, and then **clone** it so you've got the code locally.

```
$ git clone https://github.com/<your githubname>/raugustos.git
$ cd raugustos
$ gem install jekyll # If you don't have jekyll installed
$ rm -rf _site && jekyll server
```

### Modify the `_config.yml`

The _config.yml located in the root of the raugustos directory contains all of the configuration details for the Jekyll site. The defaults are:

``` yml
# Website settings
title: "Raphael Augustos"
description: "Augustos blog,use Jekyll and github pages."
keywords: "Raphael,Augustos,blog,Jekyll,github,gh-pages"

baseurl: "/"
url: "http://www.raphaelaugustos.com"
# url: "http://127.0.0.1:4000"

# author
author:
  name: 'Augustos'
  first_name: 'Augustos'
  last_name: 'Ferreira'
  email: 'augustos.raphael@gmail.com'
  facebook_username: 'raphael augustos'
  github_username: 'raugustos'
  head_img: 'static/img/landing/augustos.jpg'


# landing page
landing:
  home: 'Home'
  about: 'About'
  career: 'Career'
  skills: 'Skills'
  projects: 'Project'
  blog: 'Blog'
  contact: 'Link'

# my projects
project:
  saplatform:
    name: 'Saplatform'
    url: '/raugustos/saplatform'
    img: 'static/img/landing/saplatform.jpg'
  augustos:
    name: 'augustos'
    url: '/raugustos/raugustos'
    img: 'static/img/landing/jekyll.jpg'


# blog index
index:
  home: 'Home'
  python: 'Python'
  linux: 'Linux'
  html: 'HTML'
  database: 'Database'
  mac: 'Mac'
  life: 'Life'

...
```
### Jekyll Serve

Then, start the Jekyll Server. I always like to give the --watch option so it updates the generated HTML when I make changes.

```
$ jekyll serve --watch
```

Now you can navigate to localhost:4000 in your browser to see the site.

### Using Github Pages

You can host your Jekyll site for free with Github Pages. [Click here](https://pages.github.com) for more information.

A configuration tweak if you're using a gh-pages sub-folder

In addition to your github-username.github.io repo that maps to the root url, you can serve up sites by using a gh-pages branch for other repos so they're available at github-username.github.io/repo-name.

This will require you to modify the _config.yml like so:

``` yml
# Welcome to Jekyll!

# Site settings
title: Repo Name

baseurl: "/"
url: "http://github-username.github.io"
# url: "http://127.0.0.1:4000"

# author
author:
  name: nickname
  first_name: firstname
  last_name: lastname
  email: your_email@example.com
  facebook_username: facebook_example
  github_username: 'github_example
  head_img: 'path/of/head/img'

# landing page
landing:
  home: landing-1
  about: landing-2
  career: landing-3
  skills: landing-4
  blog: landing-5
  contact: landing-6

# blog index
index:
  home: index-1
  python: index-2
  linux: index-3
  html: index-4
  database: index-5
  mac: index-6
  life: index-7

# blog img path
img_path: '/path/of/blog/img/'
```

If you start server on localhost, you can turn on `# url: "http://127.0.0.1:4000"`.

### Pagination

The pagination in jekyll is not very perfect,so I use front-end web method,there is a [blog](http://www.raphaelaugustos.com/html/2016/06/04/jekyll-pagination-with-jpages.html) about the method and you can refer to [jPages](http://luis-almeida.github.io/jPages).


### Bilingual Page

The landing page of the blog is bilingual page,when you click national flag,the page language changes.The fllowing is how to set up bilingual page.

#### Step 1

To add i18 support for your app you need to define what text you would like to translate. The best way to define your text is to store it in external json file. For example:

**Each language you should have own json file!**

en.json

``` json
{
  "website":{
    "title": "rAugustos"
  },
  "nav":{
    "home": "Home",
    "about_me": "About",
    "skills": "Skills",
    "career": "Career",
    "blog": "Blog",
    "contact": "Contact"
  }
}
```

pt.json

``` json
{
  "website":{
    "title": "rAugustos"
  },
  "nav":{
    "home": "Home",
    "about_me": "Sobre mim",
    "skills": "Habilidades",
    "career": "Carreira",
    "blog": "Blog",
    "contact": "Contato"
  }
}
```

#### Step 2

Next you need to add html indicators in all place you want to use i18.(index.html)

``` html
<a class="navbar-brand" href="#page-top" id="i18_title"><span data-i18n="website.title">{{ site.title }}</span></a>
```

#### Step 3

Next you need to initialise the i18next plugin:
json files are located in `static/locales` folder.

``` javascript
$.i18n.init(
    resGetPath: 'locales/__lng__.json',
    load: 'unspecific',
    fallbackLng: false,
    lng: 'en'
}, function (t)
    $('#i18_title').i18n();
});
```

#### Step 4

After that if you want to change the language you just need to add buttons and fire the i18n.setLng() function.

HTML markup

``` html
<a class="btn btn-sm set_en"><img src="{{"static/img/flags/64/United-States.png"| prepend: site.baseurl }}" height="16px" width="16px"></a>
<a class="btn btn-sm set_pt"><img src="{{"static/img/flags/64/Brazil.png"| prepend: site.baseurl }}" height="16px" width="16px"></a>
```

Javascript code

``` javascript
$('.set_en').on('click', function (){
    i18n.setLng('en', function(){

        $('#i18_title').i18n();

   });
});

$('.set_cn').on('click', function (){
    i18n.setLng('pt', function(){

        $('#i18_title').i18n();

    });
});
```

Link: [i18next](http://i18next.github.io/i18next/)


### Enjoy

I hope you enjoy using rAgustos. If you encounter any issues, please feel free to let me know by creating an issue. I'd love to help.



## Thanks to the following

* [Jekyll](http://jekyllrb.com)
* [Bootstrap](http://www.bootcss.com)
* [jPages](http://luis-almeida.github.io/jPages)
* [i18next](http://i18next.github.io/i18next)
* [pixyll](https://github.com/johnotander)
* [androiddevelop](https://github.com/androiddevelop)



