### MY NOTE

_Проверка markdown_

Про загрузку множественных файлов:
```javascript
function MultipleFiles(array $_files, $top = TRUE)
    {
        $files = array();
        foreach($_files as $name=>$file){
            if($top)
                $sub_name = $file['name'];
            else
                $sub_name = $name;
            if(is_array($sub_name)){
                foreach(array_keys($sub_name) as $key){
                    $files[$name][$key] = array(
                        'name'     => $file['name'][$key],
                        'type'     => $file['type'][$key],
                        'tmp_name' => $file['tmp_name'][$key],
                        'error'    => $file['error'][$key],
                        'size'     => $file['size'][$key],
                    );
                    $files[$name] = MultipleFiles($files[$name], FALSE);
                }
            }else{
                $files[$name] = $file;
            }
        }
        return $files;
    }
```
