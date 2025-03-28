### Установка плагинов без плагин-менеджера 

1. В корневом каталоге, в папке .vim создать каталог bundle (~/.vim/bundle) 

2. Копировать плагины в папку bundle (~/.vim/bundle/<ur_plug_here>)

3. Необходимо указать для vim место, где искать плагины. Это делается коммандой
   runtimepath. Так же с помощью нее можно посмотреть уже внесенные в билд пути
   для поиска (:set runtimepath?).

Для установки нового пути для плагина в конфиге vim
нужно прописать : set runtimepath^=~/.vim/bundle/<plug_name>.vim

> Путь до .vim-файла может отличаться. Например так :
> ~/.vim/bundle/plugin/<plug_name>.vim


=================================================
### Быстрое копирование/перемещение строк по результату поиска:

:g/pattern/t$ - скопировать все строки с совпадением в конец файла

:g/pattern/m$ - переместить все строки с совпадением в конец файла

:g/pattern/d - удалить все строки с совпадением

:g/^$/d - удалить все пустые строки

:g/^\_$\n\_^$/d - заменить две пустых строки подряд на одну

Быстрый поиск строки по содержанию 
/^[^#]*pattern



=================================================
### fzf доп. настройки :

поиск дотфайлов:
export FZF_DEFAULT_COMMAND='ag --hidden --ignore .git -g ""'


=================================================
## Фичи (Обобщенный раздел с разными функциями) :

### Для того, чтобы быстро пронумеровать строки, например так :
	1 eggs
	2 milk
	3 bread
	4 nails
	5 notepad

Необходимо сделать следующее :
1. выделить первые буквы каждой строки (<C-v>)
2. shift+i (вход в режим ввода *ДО* выделенного)
3. ввести 0, выделить все нули (gv - выделить пред. область)
4. g<C-a>

### Генерация числовых паттернов :
	> Статья-исходник
	> https://vim.fandom.com/wiki/Making_a_list_of_numbers

Вывести числа в указанном диапазоне в столбец
	:put=range(1,5)

Сгенерировать числа от 0001 до 0150 
	:put =map(range(1,150), 'printf(''%04d'', v:val)')
	> Более детальное описание команды
	> The results range from 0001 to 0150. The map() function replaces each
	> value with the result of the expression, which must be given as a
	> string (the double '' presents a single apostrophe when inside an
	> apostrophe-quoted string). In the expression, v:val represents each
	> value from the list in the first argument.

Пример генерации чисел с неким "префиксом"
	:for i in range(1,10) | put ='192.168.0.'.i | endfor

	> Вывод :
	> 192.168.0.1
	> 192.168.0.2
	> 192.168.0.3
	> etc... 

Синхронизация двух буферов в сплит моде 
	> :set scrollbind (в обоих буферах)
