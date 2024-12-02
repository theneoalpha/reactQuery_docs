what is React Query (react TanStack query)?

   - React query is a tool
   - Modern Tool and mostly used in indsutries
   - inhances developer experiences
            : Error Handling
            : Loading
            : Data fetching
            : caching
            : retries

   - Powerful asynchronous state management for js,react, solid,vue etc.
   -          


Difference between fetch,axios and react query?
    - Fetch is a function to fetch the data from backend
    - Axios is a library to fetch the data in more precies way with error handling and all are easy
    - React query(tanstack query) is a tool to perform precise api fetching and all



Two main concept in React query

    - Query : used when we fetch the data
    - mutation : used when we have to post or update the data in server

- Feature 1 of react Query 
Easy to fetch the api 



Steps to install and use react-query

    Step 1 : install react query from npm 

                npm i @tanstack/react-query

    Step 2 : Query client ka instance banana hai     

        Step 2.1 import karenge App.js me 

                import {QueryClient, QueryClientProvider} from '@tanstack/react-query';

        Step 2.2 wrap karenge app.js ke saare component ko queryClient me

                     <QueryClientProvider client={queryClient}>
                        <Router>
                     </QueryClientProvider>   

    Step 3 : useQuery use karenge api call karne ke liye

        Step 3.1 : import karenge useQuery ko uss page me

                        import {useQuery} from '@tanstack/react-query';

        Step 3.2 : function banake use karenge useQuery ko

                         const {} = useQuery({queryKey: , queryFn: })  

                    Q. : why we use queryKey?
                    
                        - Help in caching the data
                        - Generally we pass a array jisme ek random string pass karte hai taaki vo use kar sake hum caching ke time

                    Step 3.2.1 :    const {} = useQuery({queryKey:["products"], queryFn: }) 


                    Q. what is the role of queryFn ? 

                        - through this function we fetch the data

                    Step 3.2.2 : const {} = useQuery({queryKey:["products"], queryFn: fetchProducts})

                    Step 3.2.3 : function create karenge fetchProducts

                            const fetchProducts = async ()=>{
                                const response = await fetch('https://dummyjson.com/products');

                                const data = await response.json();

                                return data.products;

- Feature 2 of useQuery : inbuild isLoading, and error handling


        Step 3.3 : isLoading and error inbuild hota hai

                const {isLoading, error, data:products} = useQuery({queryKey:['products], queryFn: fetchProducts})

                            }    


- Fetaure 3 of useQuery : Retrying
If the request is failed or api is not correct , then useQuery bydefault retry 3 times to api automatically

- Feature 4 of useQuery : Caching

react query me stale time ( a time upto which the data is cached/valid) hota hai , bydefault iski value infinity hoti hai means no caching , joki abhi change karke dekhenge

    agar hum staleTime : 10second kar de to after 10 second , caching disabled after 10 sec


    Step to use staleTime in code 


            const {isLoading, error, data:products} = useQuery({
                queryKey:['products],
                 queryFn: fetchProducts,
                 staleTime: 10000,
                 })


    Step to use staleTime globally in complete app : by defining it in app.js file


            app.js

                const queryClient = new QueryClient({
                    defaultOptions: {
                        queries: {
                            staleTime: 10000,
                        }
                    }
                })


                        










