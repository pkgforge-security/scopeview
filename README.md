### ℹ️ About
Slightly revamped vesion of TomNomNom's [scopeview](https://github.com/pkgforge-security/scopeview) in bash.<br>
Supports `scope` in **any file**, **anywhere** without any ***Installatiion / Deps***<br>
If you want a better tool, consider using [Inscope]((https://github.com/pkgforge-security/scopeview)) directly.

### 🖳 Installation
- This is single shell script, so it can be downloaded or piped to bash directly.

### 🧰 Usage
> - Generate a **`.scope`** file using [scopegen](https://github.com/pkgforge-security/scopegen)
> ```bash
> ➼ cat inscope-domains.txt
>        example.com
>        example.org
>        abc.example.com
> ➼ cat outscope-domains.txt
>        oos.example.com
>        oos.abc.example.org
>  ```
>  Then,
>  ```bash 
>  ➼ scopegen -t inscope-domains.txt -in && scopegen -t outscope-domains.txt -os | tee -a .scope
>  ``` 
>  ```bash 
> ➼ cat .scope
>        .*\.example\.com$
>        .*\.example\.org$
>        .*\.abc\.example\.com$
>        !.*oos\.example\.com$
>        !.*oos\.abc\.example\.org$
>  ```
- #### Once you have a `.scope`
```bash
!# Without using any options
!# This assumes there is a **`.scope`** file in your working directory or cwd's parent.
cat your-data-to-be-filtered.ext | scopeview
!# Or Via STDIN
cat your-data-to-be-filtered.ext | bash <(curl -qfsSL "https://raw.githubusercontent.com/pkgforge-security/scopeview/main/scopeview.sh")

!# Using -s 
cat your-data-to-be-filtered.ext | scopeview -s .scope-file
!# Or Via STDIN
cat your-data-to-be-filtered.ext | bash <(curl -qfsSL "https://raw.githubusercontent.com/pkgforge-security/scopeview/main/scopeview.sh") -s .scope-file
```